<template>
  <div class="field">
    <label class="label">
      {{ type }}
    </label>
    <div class="control">
      <div class="select is-fullwidth">
        <select name="" id="">
          <option value="">Please choose</option>
          <option
            v-for="variation in variations"
            :value="variation"
            :key="variation.id"
          >
            {{ variation.name }}
          </option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductVariation",
  props: {
    type: {
      type: String,
      required: true
    },
    variations: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
