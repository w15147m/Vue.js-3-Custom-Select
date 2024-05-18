<template>
  <div>
    <div class="container position-relative rounded-3 mt-5">
        <div 
            class="select_btn rounded-3 d-flex align-items-center justify-content-between mb-1" 
            @click="toggleDropdown"
        >
            <span class="btn_text">{{ selectedOption || 'Select an option' }}</span>
            <span class="btn_arrow d-flex align-items-center justify-content-center rounded-5 pt-1">
                <i :class="isDropdownOpen ? 'fa-solid fa-chevron-up' : 'fa-solid fa-chevron-down'"></i>
            </span>
        </div>
        <div 
            class="selected_options" 
            v-show="isDropdownOpen"
        >
            <div 
                class="option d-flex mb-1 rounded-3 d-flex align-items-center justify-content-start hover cursor-pointer" 
                v-for="(option, index) in options" 
                :key="index" 
                @click="selectOption(option)"
            >
                <p class="cursor-pointer">
                    {{ option }}
                </p>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
    modelValue: {
      default: null
    }
  },
  
  data() {
    return {
      selectedOption: this.modelValue,
      isDropdownOpen: false
    };
  },
  watch: {
    modelValue(newValue) {
      this.selectedOption = newValue;
    }
  },
  methods: {
    selectOption(option) {
      this.selectedOption = option;
      this.$emit('update:modelValue', option);
      this.isDropdownOpen = false;
    },
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen;
    }
  }
}
</script>

<style>
/* Existing styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: poppins;
}

body {
    background-color: #e3f2fd;
}

.container {
    width: 350px;
}

.select_btn {
    background-color: #fff;
    width: 100%;
    height: 50px;
    padding: 0 15px;
    cursor: pointer;
}

.btn_arrow {
    font-size: 14px;
    height: 21px;
    width: 21px;
    background: #6e93f7;
}

.selected_options {
    display: none;
}

.selected_options {
    display: block;
    background-color: #fff;
    position: absolute;
    width: 93%;
    border-radius: 20px;
    z-index: 1000;
}

.option:hover {
    background-color: #fcfcfcf8;
    border: 1px solid #fcfcfcf8;
}

.option {
    background-color: #fff;
    height: 50px;
    padding: 0 15px;
    cursor: pointer;
}
</style>
