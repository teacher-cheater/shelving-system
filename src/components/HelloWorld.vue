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
          <!-- кастомная сортировка элементов -->
          <div class="select__form-group dropdown-items">
            <div class="dropdown-items__content dropdown">
              <span>Сортировать по:</span>
              <button class="dropdown-items__btn">Цена по возрастанию</button>
              <ul class="dropdown-items__list">
                <li class="dropdown-items__item arr-top">
                  Цена по возрастанию
                </li>
                <li class="dropdown-items__item arr-down">Цена по убыванию</li>
              </ul>
            </div>
          </div>
          <!-- кастомная сортировка элементов -->
          <div class="select__form-group dropdown-items">
            <div class="dropdown-items__content dropdown">
              <span>Материал</span>
              <button class="dropdown-items__btn dropdown-items__btn--active">
                Металл
              </button>
              <ul class="dropdown-items__list">
                <li
                  class="dropdown-items__item arr-top"
                  data-value="material-steel"
                >
                  Металл
                </li>
                <li
                  class="dropdown-items__item arr-down"
                  data-value="material-tree"
                >
                  Дерево
                </li>
              </ul>
            </div>
          </div>
          <!--  -->
        </div>
      </div>
      <div class="main__cards">
        <div class="main__card product-card">
          <div class="product-card__label">Скидка</div>
          <div class="product-card__image">
            <!-- <img src="./icons/img.jpeg" alt="product" /> -->
          </div>
          <div class="product-card__info">
            <p class="product-card__article">L422WH</p>
            <p class="product-card__title">Ручка дверная</p>
            <div class="product-card__footer">
              <div class="product-card__prices">
                <p class="product-card__sale">400₽</p>
                <p class="product-card__price">355₽</p>
              </div>
              <div class="product-card__icons-choice">
                <button type="button">
                  <!-- <img src="./icons/cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/add-cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/like-empty.svg" alt="like" /> -->
                </button>
              </div>
            </div>
          </div>
        </div>

        <div class="main__card product-card">
          <div class="product-card__label">Скидка</div>
          <div class="product-card__image">
            <!-- <img src="./icons/img.jpeg" alt="product" /> -->
          </div>
          <div class="product-card__info">
            <p class="product-card__article">L422WH</p>
            <p class="product-card__title">Ручка дверная</p>
            <div class="product-card__footer">
              <div class="product-card__prices">
                <p class="product-card__sale">400₽</p>
                <p class="product-card__price">355₽</p>
              </div>
              <div class="product-card__icons-choice">
                <button type="button">
                  <!-- <img src="./icons/cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/add-cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/like-empty.svg" alt="like" /> -->
                </button>
              </div>
            </div>
          </div>
        </div>

        <div class="main__card product-card">
          <div class="product-card__label">Скидка</div>
          <div class="product-card__image">
            <!-- <img src="./icons/img.jpeg" alt="product" /> -->
          </div>
          <div class="product-card__info">
            <p class="product-card__article">L422WH</p>
            <p class="product-card__title">Ручка дверная</p>
            <div class="product-card__footer">
              <div class="product-card__prices">
                <p class="product-card__sale">400₽</p>
                <p class="product-card__price">355₽</p>
              </div>
              <div class="product-card__icons-choice">
                <button type="button">
                  <!-- <img src="./icons/cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/add-cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/like-empty.svg" alt="like" /> -->
                </button>
              </div>
            </div>
          </div>
        </div>

        <div class="main__card product-card">
          <div class="product-card__label">Скидка</div>
          <div class="product-card__image">
            <!-- <img src="./icons/img.jpeg" alt="product" /> -->
          </div>
          <div class="product-card__info">
            <p class="product-card__article">L422WH</p>
            <p class="product-card__title">Ручка дверная</p>
            <div class="product-card__footer">
              <div class="product-card__prices">
                <p class="product-card__sale">400₽</p>
                <p class="product-card__price">355₽</p>
              </div>
              <div class="product-card__icons-choice">
                <button type="button">
                  <!-- <img src="./icons/cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/add-cart.svg" alt="cart" /> -->
                </button>
                <button type="button">
                  <!-- <img src="./icons/like-empty.svg" alt="like" /> -->
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HelloWorld",
  props: {
    msg: String,
  },
});
</script>

<style scoped>
/* @font-face {
  font-family: "SF Pro Display";
  src: url("./fonts/SF-Pro-Display-Regular.otf") format("opentype");
} */

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  border: 0;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

li {
  list-style: none;
}

a,
a:visited {
  text-decoration: none;
}

a:hover {
  text-decoration: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-weight: inherit;
  font-size: inherit;
}

html,
body {
  height: 100%;
  /* font-family: "SF Pro Display"; */
}

html {
  font-size: 16px;
}

.header {
}

[class*="__container"] {
  max-width: 1490px;
  margin: 0px auto;
}

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
  /* font-family: "SF Pro Display"; */
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

.product-card {
  border: 1px solid rgb(210, 210, 210);
  position: relative;

  height: 352px;
  overflow: hidden;
  display: grid;
  grid-template-rows: 1fr 1fr;
  transition: 0.8s cubic-bezier(0.2, 0.8, 0.2, 1);
}

.product-card:hover {
  transform: scale(1.035, 1.035);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
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

.product-card__price {
}

.product-card__icons-choice {
  display: flex;
  gap: 27px;
}

.product-card__icons-choice button {
  background: transparent;
  cursor: pointer;
}
</style>
