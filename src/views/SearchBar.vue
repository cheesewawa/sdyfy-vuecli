<template>
  <div class="search bar7">
    <form>
      <input type="text" v-model="inputValue" :placeholder="aaa" />
      <button class="searchbutton" @click="clickMethod"></button>
    </form>
  </div>
</template>

<script>
import { defineComponent } from "@vue/composition-api";

export default defineComponent({
  props: {
    callback: {
      type: Function,
    },
  },
  data() {
    return {
      inputValue: "",
    };
  },
  methods: {
    clickMethod() {
      this.callback(this.inputValue);
    },
  },
  setup() {},
});
</script>
