<template>
  <div class="dropdown-items">
    <div class="dropdown-items__content dropdown">
      <span>{{ label }}</span>
      <button
        class="dropdown-items__btn"
        @click="toggleDropdown"
        :class="{ 'dropdown-items__btn--active': isOpen }"
      >
        {{ selectedItem || defaultText }}
      </button>
      <ul
        class="dropdown-items__list"
        :class="{ 'dropdown-items__list--visible': isOpen }"
      >
        <li
          v-for="item in items"
          :key="item"
          class="dropdown-items__item"
          @click="selectItem(item)"
        >
          {{ item }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Dropdown",
  props: {
    items: {
      type: Array as () => string[],
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
    defaultText: {
      type: String,
      required: true,
    },
  },
  setup(props, { emit }) {
    const isOpen = ref(false);
    const selectedItem = ref<string | null>(null);

    const toggleDropdown = () => {
      isOpen.value = !isOpen.value;
    };

    const selectItem = (item: string) => {
      selectedItem.value = item;
      isOpen.value = false;
      emit("update:selected", item);
    };

    const handleClickOutside = (event: MouseEvent) => {
      const target = event.target as HTMLElement;
      if (!target.closest(".dropdown")) {
        isOpen.value = false;
      }
    };

    const handleKeyDown = (event: KeyboardEvent) => {
      if (event.key === "Tab" || event.key === "Escape") {
        isOpen.value = false;
      }
    };

    document.addEventListener("click", handleClickOutside);
    document.addEventListener("keydown", handleKeyDown);

    return {
      isOpen,
      selectedItem,
      toggleDropdown,
      selectItem,
    };
  },
});
</script>

<style scoped>
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
  background: url("../assets/icons/chevron-bottom.svg") 0 0 / contain no-repeat;
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
</style>
