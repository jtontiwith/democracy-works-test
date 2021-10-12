<template>
  <div class="max-w-5xl mx-auto sm:px-6 lg:px-8 py-6">
    <h1 class="mb-4 text-3xl">Democracy Works Elections API Query</h1>
    <form class="bg-gray-100 p-4">
      <BaseInput
        v-for="field in formFields"
        :key="field"
        v-model="formValues[field]"
        :label="field"
        :name="field"
        class="mb-4"
      />
      <BaseButton @click.native="getResults">Submit</BaseButton>
    </form>
    <template v-if="result">
      <ul class="mt-6">
        <li v-for="(value, name, index) in result" :key="index">
          <span class="font-bold">{{ name }}</span> : <span>{{ value }}</span>
        </li>
      </ul>
    </template>
  </div>
</template>

<script>
export default {
  name: 'ElectionsSearch',
  data: () => ({
    formValues: {
      country: '',
      state: '',
      city: '',
    },
    result: null,
  }),
  fetchOnServer: false,
  async fetch() {
    const [country, state, city] = Object.values(this.formValues).map((f) =>
      f.toLowerCase()
    )

    if (!country || !state || !city) return

    this.result = await fetch(
      `https://ygfhydmrke.execute-api.us-east-2.amazonaws.com/dev/demo-works?country=${country}&state=${state}&city=${city}`
    ).then((res) => res.json())
  },
  computed: {
    formFields() {
      return Object.keys(this.formValues)
    },
  },
  methods: {
    getResults() {
      this.$fetch()
    },
  },
}
</script>
