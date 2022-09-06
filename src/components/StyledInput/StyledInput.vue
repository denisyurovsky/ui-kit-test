<template>
  <div class="wrapper">
    <label for="input" :class="{labelError: isInvalid}" class="inputName">{{inputName}}</label>
    <div class="input__wrapper">
      <input
          class="input"
          v-model="text"
          :readonly="locked"
          :class="{locked: locked, inputError: isInvalid}"
          :disabled="disabled"
          id="input"
          @input="updateValue"
          :type="inputType"
          :placeholder="placeholder" />
      <div class="clear-button" v-show="text.length > 0 && !isInvalid" @click="clearField">x</div>
      <div class="error" v-show="isInvalid"
      >!</div>
    </div>
    <span class="errorName" :style="{ visibility: isInvalid ? 'visible' : 'hidden'}">{{ errorName }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: '',
    }
  },
  methods: {
    updateValue() {
     this.$emit('update:modelValue', event.target.value)
    },
    clearField() {
      this.text = ''
      this.$emit('update:modelValue', '')
    },
  },
  props: {
    placeholder: {
      type: String,
      default: ''
    },
    inputName: {
      type: String,
      default: ''
    },
    errorName: {
      type: String,
      default: ''
    },
    inputType: {
      type: String,
      default: 'text'
    },
    disabled: {
      type: Boolean,
      default: false
    },
    locked: {
      type: Boolean,
      default: false
    },
    pattern: {
      type: String,
    },
    isInvalid: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped lang="scss">
@import '_variables';

.inputName {
  color: $gray;
  font-size: 12px;
  display: block;
  align-self: flex-start;
}

.input__wrapper {
  position: relative;
}

.labelError, .error {
  color: $error;
}
.clear-button, .error {
  position: absolute;
  right: 8px;
  top: 1px;
}

.inputError {
  border-color: $error;
}

.wrapper {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.errorName {
  align-self: flex-end;
  font-size: 12px;
  color: $error;
}

input {
  padding: 5px 4px;
  border: 0.5px solid $gray;
  border-radius: 4px;
  color: $input-primary;
  outline: none !important;

  transition: all 0.5s ease;

  &:disabled {
    color: $gray;
    border: 0.5px solid $gray;
    background: $disabled;
    cursor: not-allowed;
  }

  &:hover:not(:disabled), &:hover:not(:read-only) {

    border: 0.5px solid $primary;
  }
  &:focus {
    box-shadow: 0 0 1px $primary;
  }
}

.locked, .locked:focus {
  border: none !important;
  box-shadow: none;
}

</style>