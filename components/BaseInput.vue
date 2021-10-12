<template>
  <div>
    <label for="email" class="block font-bold text-gray-700">{{ label }}</label>
    <div class="mt-1">
      <input
        id="email"
        type="text"
        :name="name"
        class="
          block
          w-full
          py-3
          pl-2
          placeholder-gray-300
          border-gray-300
          rounded-sm
          shadow-sm
          focus:ring-indigo-500 focus:border-indigo-500
        "
        :placeholder="placeholder"
        aria-describedby="email-description"
        :value="value"
        v-bind="$attrs"
        v-on="inputListeners"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'BaseInput',
  inheritAttrs: false,
  props: {
    label: {
      type: String,
      default: 'label',
    },
    name: {
      type: String,
      default: 'name',
    },
    placeholder: {
      type: String,
      default: '',
    },
    value: {
      type: String,
      default: '',
    },
  },
  computed: {
    inputListeners() {
      const vm = this
      return Object.assign({}, this.$listeners, {
        input(event) {
          vm.$emit('input', event.target.value)
        },
      })
    },
  },
}
</script>
