<template>
 <h1>UI KIT</h1>
  <div class="content__wrapper">
    <div class="example__wrapper">
      <h1>DEFAULT</h1>
      <StyledButton
          variant="default"
          text="default" />
      <StyledButton
          variant="default"
          :disabled="true"
          text="default disabled" />
    </div>
    <div class="example__wrapper">
      <h1>NORMAL</h1>
      <StyledButton variant="normal"
                    text="normal"/>
      <StyledButton variant="normal"
                    :disabled="true"
                    text="normal disabled"/>
      <StyledButton variant="normal"
                    iconPath="plus-icon.svg"
                    text="normal with icon" />
      <StyledButton variant="normal"
                    iconPath="bluetooth.svg"
                    text="button with another icon" />
      <StyledButton variant="normal"
                    :disabled="true" iconPath="plus-icon-disabled.svg"
                    text="normal with icon disabled" />
    </div>
    <div class="example__wrapper">
      <h1>LINK</h1>
      <StyledButton variant="link"
                    text="link" />
      <StyledButton variant="link"
                    :disabled="true"
                    text="link disabled"/>
    </div>
    <div class="example__wrapper">
      <h1>Input</h1>
      <StyledInput
          v-model="text"
          inputType="text"
          inputName="Email"
          placeholder="enter an email"
          errorName="email Is invalid" />
      <span>здесь будет выведен текст из инпута</span>
      {{text}}
      <StyledInput
          :disabled="true"
          inputType="text"
          inputName="Email"
          placeholder="enter an email"
          errorName="email Is invalid" />
      <StyledInput
          :isInvalid="true"
          inputType="text"
          inputName="Provide a number"
          placeholder="Input with error state"
          errorName="only numbers" />
      <StyledInput
          :locked="true"
          inputType="text"
          inputName="Email"
          placeholder="value is locked"
          />
    </div>
  </div>
</template>

<script>

import StyledButton from "@/components/StyledButton/StyledButton";
import StyledInput from "@/components/StyledInput/StyledInput";
export default {
  name: 'App',
  components: {StyledInput, StyledButton},
  data() {
    return {
      text: ''
    }
  }
}
</script>

<style lang="scss">

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: "Segoe UI", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.example__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  gap: 20px;
  flex-wrap: wrap;
  border-bottom: 1px solid black;
}



</style>
