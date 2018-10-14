<template>
  <div class="topbar-wrapper">
    <p>{{changed}}</p>
    <input
            @input="handleInput"
            @change="handleChange"
            v-model="innerValue"/>
  </div>
</template>

<script>
export default {
  name: 'topbar',
  props: {
    value: {
      type: String,
    }
  },
  data() {
    return {
      innerValue: this.value,
      changed: null
    }
  },
  methods: {
    handleInput() {
      // this.$emit('input', this.innerValue)
    },
    handleChange() {
      this.$emit('change', this.innerValue)
      this.changed=this.innerValue
    }
  }
}
</script>

<style lang="scss" scoped>
.topbar-wrapper {
  display: block;
  position: fixed;
  top: 0;
  width: 100%;
  height: 15rem;
  background: red;
  p {
    margin: 1rem;
    font-size: 10rem;
  }
}
</style>
