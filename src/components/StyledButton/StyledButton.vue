<template>
  <button :class="variant" :disabled="disabled">
    <!--   можно также подключить vue-svg-loader и импортировать svg как компонент-->
    <img v-if="iconPath && variant === 'normal'" :src="require('@/assets/' + iconPath)" alt="icon missing"/>
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "StyledButton",
  props: {
    variant: {
      type: String,
      default: "default",
    },
    text: {
      type: String,
      required: true,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    iconPath: {
      type: String,
      default: "",
    },
  },
};
</script>

<style scoped lang="scss">
@import "_variables";

button {
  border: none;
  font-size: 14px;
  box-sizing: border-box;
  transition: all 0.5s ease;
}

img {
  max-height: 20px;
}

.default,
.normal,
.link {
  height: 32px;
  display: flex;
  align-items: center;
  gap: 6px;
  cursor: pointer;
}

.default,
.normal {
  border-radius: 6px;
  padding: 0 20px;
}

.default {
  background-color: $primary;
  border: 1px solid $primary;
  box-shadow: 0 8px 16px rgba(143, 149, 178, 0.15);
  color: white;
  &:hover:not(:disabled) {
    box-shadow: 0 4px 16px $box-shadow;
  }
  &:focus {
    border: 1px solid $primary-dark;
  }
  &:active {
    background: $primary-dark;
  }
  &:disabled {
    background: $primary-disabled;
    border: 1px solid $primary-disabled;
    cursor: default;
  }
}

.normal {
  color: $primary;
  background: white;
  border: 1px solid $primary;
  border-radius: 6px;

  &:hover:not(:disabled) {
    box-shadow: 0 4px 16px $box-shadow;
  }
  &:focus {
    border: 1px solid $primary-dark;
  }
  &:active {
    background: $primary-active;
  }
  &:disabled {
    border: 1px solid $primary-disabled;
    background: #ffffff;
    color: $primary-disabled;
    cursor: default;
  }
}

.link {
  border: none;
  color: $primary;
  background-color: white;
  &:hover {
    // если добавить font-weight: bold то, контент кнопки сдвигать другие элементы из-за увеличения ширины контейнера
    text-shadow: .6px 0 .1px;

  }
  &:active:not(:disabled) {
    text-shadow: .6px 0 .1px;
    color: $primary-dark;
  }
  &:focus {
    color: $primary-dark;
  }
  &:disabled {
    color: $link-disabled;
    font-weight: 400;
    cursor: default;
  }
}
</style>
