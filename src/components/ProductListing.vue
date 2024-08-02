<template>
  <header class="header">
    <div class="header__container">
      <BreadCrumbs />
    </div>
  </header>

  <main class="main">
    <div class="main__container">
      <div class="main__header-block">
        <h1>Комплекты стеллажных систем</h1>
        <div class="main__right-block select">
          <DropdownList
            label="Сортировать по:"
            :items="sortOptions"
            defaultText="Цена по возрастанию"
            @update:selected="sortItems"
          />
          <DropdownList
            label="Материал"
            :items="materialOptions"
            defaultText="Металл"
            @update:selected="filterByMaterial"
          />
        </div>
      </div>

      <div class="main__cards">
        <ProductCard
          v-for="item in filteredItems"
          :key="item.id"
          :product="item"
        />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { computed, defineComponent, ref } from "vue";
import items from "../data/items.json";
import materials from "../data/materials.json";
import ProductCard from "./ProductCard.vue";
import DropdownList from "./DropdownList.vue";
import BreadCrumbs from "./BreadCrumbs.vue";

export default defineComponent({
  name: "ProductListing",
  components: {
    BreadCrumbs,
    ProductCard,
    DropdownList,
  },
  setup() {
    const sortOptions = ref(["Цена по возрастанию", "Цена по убыванию"]);
    const materialOptions = ref(materials.map(material => material.name));
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

.main__cards {
  padding: 23px 0;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(336px, 1fr));
  grid-gap: 48px;
}

@media (max-width: 800px) {
  .main__right-block {
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
  }
  .main__header-block h1 {
    font-size: 28px;
    margin-bottom: 20px;
  }
}

@media (max-width: 616px) {
  .main__right-block {
    justify-content: center;
  }
  .dropdown-items {
    width: 100%;
  }
}
</style>
