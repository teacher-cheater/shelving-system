<template>
  <div class="main__card product-card">
    <div v-if="product.price.old_price" class="product-card__label">Скидка</div>
    <div class="product-card__image">
      <img :src="product.image.url" :alt="product.name" />
    </div>
    <div class="product-card__info">
      <p class="product-card__article">{{ product.code }}</p>
      <p class="product-card__title">{{ product.name }}</p>
      <div class="product-card__footer">
        <div class="product-card__prices">
          <p v-if="product.price.old_price" class="product-card__sale">
            {{ product.price.old_price }}₽
          </p>
          <p class="product-card__price">{{ product.price.current_price }}₽</p>
        </div>
        <div class="product-card__icons-choice">
          <button @click="toggleCart" type="button">
            <img
              v-if="isInCart"
              src="../assets/icons/add-cart.svg"
              alt="add-cart"
            />
            <img v-else src="../assets/icons/cart.svg" alt="cart" />
          </button>
          <button @click="toggleFavorites" type="button">
            <img
              v-if="isFavorite"
              class="product-card__like"
              src="../assets/icons/like.svg"
              alt="like"
            />
            <img
              v-else
              class="product-card__like"
              src="../assets/icons/like-empty.svg"
              alt="empty-like"
            />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, PropType, ref } from "vue";

interface Price {
  old_price: number | null;
  current_price: number;
}

interface Image {
  url: string | undefined;
}

interface Item {
  id: string;
  name: string;
  code: string | null;
  price: Price;
  image: Image;
  material: number;
}

export default defineComponent({
  name: "ProductCard",
  props: {
    product: {
      type: Object as PropType<Item>,
      required: true,
    },
  },
  setup(props) {
    const isInCart = ref(false);
    const isFavorite = ref(false);

    onMounted(() => {
      isFavorite.value = checkLocalStorage(`favorite-${props.product.id}`);
      isInCart.value = checkLocalStorage(`cart-${props.product.id}`);
    });

    const checkLocalStorage = (key: string): boolean => {
      return localStorage.getItem(key) !== null;
    };

    const toggleCart = () => {
      isInCart.value = !isInCart.value;
      updateLocalStorage(`cart-${props.product.id}`, isInCart.value);
    };

    const toggleFavorites = () => {
      isFavorite.value = !isFavorite.value;
      updateLocalStorage(`favorite-${props.product.id}`, isFavorite.value);
    };

    const updateLocalStorage = (key: string, isActive: boolean) => {
      isActive
        ? localStorage.setItem(key, props.product.name)
        : localStorage.removeItem(key);
    };

    return {
      isInCart,
      isFavorite,
      toggleCart,
      toggleFavorites,
    };
  },
});
</script>

<style scoped>
.product-card {
  border: 1px solid rgb(210, 210, 210);
  position: relative;

  height: 352px;
  overflow: hidden;
  display: grid;
  grid-template-rows: 1fr 1fr;
  transition: 0.8s cubic-bezier(0.2, 0.8, 0.2, 1);
}

.product-card__label {
  position: absolute;
  top: 8px;
  left: 0.4px;
  background: rgb(235, 87, 87);
  color: rgb(255, 255, 255);
  font-size: 14px;
  font-weight: 500;
  line-height: 130%;
  padding: 3px 15px;
}

.product-card__image {
  padding: 9px 49px;
  width: 238px;
  height: 237px;
}

.product-card__info {
  padding: 9px 12px;
}

.product-card__article {
  color: rgb(136, 136, 136);
  font-size: 10px;
  font-weight: 400;
  line-height: 140%;
  margin-bottom: 6px;
}

.product-card__title {
  color: rgb(0, 0, 0);
  font-size: 16px;
  font-weight: 500;
  line-height: 140%;
  margin-bottom: 9px;
}

.product-card__footer {
  display: flex;
  justify-content: space-between;
}

.product-card__prices {
  display: flex;
  gap: 9px;
}

.product-card__sale {
  color: rgb(136, 136, 136);
  font-size: 16px;
  font-weight: 400;
  line-height: 140%;
  text-decoration-line: line-through;
}

.product-card__icons-choice {
  display: flex;
  gap: 27px;
}

.product-card__icons-choice button {
  background: transparent;
  cursor: pointer;
}
.product-card__icons-choice button img {
  width: 21.6px;
  height: 21.6px;
}

@media (hover: hover) {
  .product-card:hover {
    transform: scale(1.035, 1.035);
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
  }

  .product-card:active {
    transform: scale(1.035, 1.035);
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
  }
}
</style>
