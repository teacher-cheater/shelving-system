<template>
  <header class="header">
    <div class="header__container">
      <nav class="breadcrumb" aria-label="breadcrumb">
        <ol>
          <li><a href="/">Главная</a></li>
          <li><a href="/storage-systems">Системы хранения</a></li>
          <li aria-current="page">Комплекты стеллажных систем</li>
        </ol>
      </nav>
    </div>
  </header>

  <main class="main">
    <div class="main__container">
      <div class="main__header-block">
        <h1>Комплекты стеллажных систем</h1>
        <div class="main__right-block select">
          <Dropdown
            label="Сортировать по:"
            :items="sortOptions"
            defaultText="Цена по возрастанию"
            @update:selected="sortItems"
          />
          <Dropdown
            label="Материал"
            :items="materialOptions"
            defaultText="Металл"
            @update:selected="filterByMaterial"
          />
        </div>
      </div>

      <div class="main__cards">
        <ProductCard v-for="item in items" :key="item.id" :product="item" />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { computed, defineComponent, ref } from "vue";
import items from "../data/items.json";
import ProductCard from "./ProductCard.vue";
import Dropdown from "./Dropdown.vue";

export default defineComponent({
  name: "HelloWorld",
  components: {
    ProductCard,
    Dropdown,
  },
  setup() {
    const sortOptions = ref(["Цена по возрастанию", "Цена по убыванию"]);
    const materialOptions = ref(["Металл", "Дерево"]);
    const selectedSort = ref("");
    const selectedMaterial = ref("");
    const itemsList = ref(items);

    const sortItems = (sortOption: string) => {
      selectedSort.value = sortOption;
    };

    const filterByMaterial = (materialOption: string) => {
      selectedMaterial.value = materialOption;
    };

    const filteredItems = computed(() => {
      let filtered = itemsList.value;

      if (selectedMaterial.value === "Металл") {
        filtered = filtered.filter(
          (item: { material: number }) => item.material === 2
        );
      } else if (selectedMaterial.value === "Дерево") {
        filtered = filtered.filter(
          (item: { material: number }) => item.material === 1
        );
      }

      if (selectedSort.value === "Цена по возрастанию") {
        filtered.sort(
          (
            a: { price: { current_price: number } },
            b: { price: { current_price: number } }
          ) => a.price.current_price - b.price.current_price
        );
      } else if (selectedSort.value === "Цена по убыванию") {
        filtered.sort(
          (
            a: { price: { current_price: number } },
            b: { price: { current_price: number } }
          ) => b.price.current_price - a.price.current_price
        );
      }

      return filtered;
    });

    return {
      items,
      sortOptions,
      materialOptions,
      sortItems,
      filterByMaterial,
      filteredItems,
    };
  },
});
</script>

<style scoped>
.header__container {
  padding: 32px 15px;
}

.breadcrumb ol {
  display: flex;
  gap: 30px;
}

.breadcrumb ol li {
  position: relative;
}

.breadcrumb ol li a {
  color: rgb(130, 130, 130);
}

.breadcrumb ol li:not(:last-child)::after {
  content: "";
  position: absolute;
  display: block;
  top: 1px;
  right: -17px;
  width: 2px;
  height: 95%;
  background-color: rgb(130, 130, 130);
  transform: rotate(19deg);
}

.main__container {
  padding: 0px 15px;
}

.main__header-block h1 {
  color: rgb(0, 0, 0);
  font-size: 36px;
  font-weight: 600;
  line-height: 48px;
  letter-spacing: 0px;
  text-align: left;
  margin-bottom: 32px;
}

.main__right-block {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  gap: 10px;
}

@media (max-width: 800px) {
  .main__right-block {
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
  }
}

.dropdown-items__content {
  position: relative;
}

.dropdown-items__content span {
  display: flex;
  color: rgb(79, 79, 79);
  font-size: 12px;
  font-weight: 400;
  line-height: 150%;
  letter-spacing: 3%;
  text-align: left;
  padding: 6px 16px;
}

.dropdown-items__btn {
  position: relative;
  display: block;
  text-align: left;
  min-width: 288px;
  width: 100%;
  background: #f2f2f2;
  padding: 10px 16px;
  font-size: 14px;
  line-height: 1.5;
  color: #000000;
  cursor: pointer;
}

.dropdown-items__btn:hover {
  -webkit-transition: all 0.4s ease-in 0s;
  -o-transition: all 0.4s ease-in 0s;
  transition: all 0.4s ease-in 0s;
  -webkit-box-shadow: 1px 4px 4px rgba(54, 94, 125, 0.1);
  box-shadow: 1px 4px 4px rgba(54, 94, 125, 0.1);
}

.dropdown-items__btn::before {
  content: "";
  position: absolute;
  top: 50%;
  right: 10px;
  -webkit-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
  width: 24px;
  height: 24px;
  /* background: url("./icons/chevron-bottom.svg") 0 0 / contain no-repeat; */
  pointer-events: none;
  z-index: 1;
}

.dropdown-items__btn:focus {
  outline: none;
  -webkit-box-shadow: 0px 0px 0px 3px rgba(54, 94, 125, 0.1);
  box-shadow: 0px 0px 0px 3px rgba(54, 94, 125, 0.1);
}

.dropdown-items__list {
  display: none;
  position: absolute;
  left: 0;
  top: 75px;
  padding: 10px;
  background: #ffffff;
  -webkit-box-shadow: 1px 4px 40px rgba(54, 94, 125, 0.1);
  box-shadow: 1px 4px 40px rgba(54, 94, 125, 0.1);
  overflow: hidden;
  width: 100%;
  z-index: 5;
}

.dropdown-items__item {
  padding: 8px;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.17;
  color: #080534;
  cursor: pointer;
}

.dropdown-items__item:hover {
  background: #f3f6f8;
}

.dropdown-items__input {
  display: none;
}

.dropdown-items__list--visible {
  display: block;
}

.dropdown-items__btn--active {
  outline: none;
  -webkit-box-shadow: 0px 0px 0px 3px rgba(54, 94, 125, 0.1);
  box-shadow: 0px 0px 0px 3px rgba(54, 94, 125, 0.1);
}

.main__cards {
  padding: 23px 0;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(329px, 1fr));
  grid-gap: 48px;
}
</style>
