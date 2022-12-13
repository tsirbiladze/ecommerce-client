<template>
  <div class="field">
    <label class="label">
      {{ type }}
    </label>
    <div class="control">
      <div class="select is-fullwidth">
        <select :value="selectedVariationId"  @change="changed($event, $type)">
          <option value="">Please choose</option>
          <option
            v-for="variation in variations"
            :value="variation.id"
            :key="variation.id"
          >
            {{ variation.name }}

            <template v-if="variation.price_varies">
              ({{ variation.price }})
            </template>
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
    },
    value: {
      required: false,
      default: ''
    }
  },

  computed: {
    selectedVariationId() {
      if (!this.findVariation(this.value.id)) {
        return ''
      }

      return this.value.id
    }
  },

  methods: {
    changed(event, type) {
      this.$emit('input', this.findVariation(event.target.value))
    },


    findVariation(id) {
      let variation = this.variations.find(v => v.id == id)

      if (typeof variation === 'undefined') {
        return null
      }

      return variation
    }

  }
}
</script>

<style scoped>

</style>
