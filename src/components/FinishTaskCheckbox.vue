<template>
  <ul id="list">
    <li class="item">
      <!-- <span class="text"></span> -->
      <div class="custom-checkbox">
        <input
          type="checkbox"
          v-model="checkboxValue"
          :disabled="isDisable"
        /><svg viewBox="0 0 35.6 35.6">
          <circle class="background" cx="17.8" cy="17.8" r="17.8"></circle>
          <circle class="stroke" cx="17.8" cy="17.8" r="14.37"></circle>
          <polyline
            class="check"
            points="11.78 18.12 15.55 22.23 25.17 12.87"
          ></polyline>
        </svg>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: "BaseCheckbox",
  props: {
    isDisable: {
      type: Boolean,
      required: false,
      default: false,
    },
    value: {
      type: Boolean,
      required: true,
    },
  },
  computed: {
    checkboxValue: {
      get() {
        return this.value
      },
      set(value) {
        this.$emit("input", value)
      },
    },
  },
}
</script>

<style lang="scss" scoped>
#list {
  display: flex;
  padding-bottom: 0.2rem;
  justify-content: space-between;
  .item {
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    .text {
      opacity: 0.4;
      margin-top: 10px;
      font-size: 12px;
      font-weight: bold;
      transition: ease all 0.2s;
      -webkit-transition: ease all 0.2s;
    }
    &:hover:enabled {
      .text {
        opacity: 1;
      }
      .custom-checkbox {
        .check {
          stroke-dashoffset: 0;
        }
      }
    }
  }
}

.custom-checkbox {
  position: relative;
  display: inline-block;
  width: 15px;
  height: 15px;
  .background {
    fill: #E8E8E8;
    stroke-width: 2px;
    transition: ease all 0.6s;
    -webkit-transition: ease all 0.6s;
  }
  .stroke {
    fill: none;
    stroke: #fff;
    stroke-miterlimit: 10;
    stroke-width: 2px;
    stroke-dashoffset: 100;
    stroke-dasharray: 100;
    transition: ease all 0.6s;
    -webkit-transition: ease all 0.6s;
  }
  .check {
    fill: none;
    stroke: #fff;
    stroke-linecap: round;
    stroke-linejoin: round;
    stroke-width: 2px;
    stroke-dashoffset: 22;
    stroke-dasharray: 22;
    transition: ease all 0.6s;
    -webkit-transition: ease all 0.6s;
  }
  input[type="checkbox"] {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    margin: 0;
    opacity: 0;
    -appearance: none;
    -webkit-appearance: none;

    &:hover:enabled {
      cursor: pointer;
    }

    &:checked {
      & + svg {
        .background {
          fill: #1abc9c;
        }
        .stroke {
          stroke-dashoffset: 0;
        }
        .check {
          stroke-dashoffset: 0;
        }
      }
    }
  }
}
</style>
