<template>
 <select v-model="modelValue" @change="changeOptions">
   <option disabled value="">Выбери из списка</option>
   <option
       :key="option.value"
       v-for="option in options"
       :value="option.value"
   >
     {{ option.name }}
   </option>
 </select>
</template>

<script>
export default {
  name: "Select",
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOptions(e) {
      this.$emit("update:modelValue", e.target.value)
    }
  }
}
</script>

<style scoped>

</style>