<template>
  <label class="checkbox">
    {{ text }}
    <input type="checkbox" class="checkbox__input" @change="$emit('input', $event)" :checked="checked">
    <span class="checkbox__checkmark"></span>
  </label>
</template>
<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    },
    checked: {
      type: Boolean,
      default: false
    }
  }
}
</script>
<style lang="scss" scoped>
.checkbox {
  display: flex;
  align-items: center;
  position: relative;
  padding-left: 35px;
  cursor: pointer;
  font-size: 12px;
  user-select: none;
  width: 100%;
  height: 100%;

  &__input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;

    &:checked ~ .checkbox__checkmark {
      background-color: #55BB06;
      border: none;

      &:after {
        display: block;
        border-color: white;
        opacity: 1;
      }
    }
  }

  &:hover{
    .checkbox__input:checked ~ .checkbox__checkmark {
      background-color: #55BB06;

      &:after {
        transform: rotate(90deg);
        width: 0;
        top: 2px;
        left: 5px;
        height: 7px;
        border-width: 0 2px 0 0;
        border-color: #fff;
      }
    }

    & .checkbox__checkmark:after {
      display: block;
      border-color: gray;
      opacity: 1;
      left: 3.5px;
      top: .5px;
      width: 2px;
      height: 6px;
      border-style: solid;
      border-width: 0 2px 2px 0;
      transform: rotate(45deg);
      transition: all 0.3s;
    }
  }

  & .checkbox__checkmark {
    position: absolute;
    top: calc(50% - 6px);
    left: 0;
    height: 12px;
    width: 12px;
    background: #FFFFFF;
    border: 1px solid #B9B9B9;
    box-sizing: border-box;
    border-radius: 2px;
    margin-left: 12px;

    &:after {
      content: "";
      position: absolute;
      opacity: 0;
      left: 4px;
      top: 1px;
      width: 2px;
      height: 6px;
      border-style: solid;
      border-width: 0 2px 2px 0;
      transform: rotate(45deg);
      transition: all 0.2s;
    }
  }
}
</style>
