<template>
  <button
    type="button"
    class="
      px-4
      py-2
      text-sm
      font-medium
      text-white
      bg-indigo-600
      border border-transparent
      rounded-sm
      shadow-sm
      hover:bg-indigo-700
      focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500
    "
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  // inline-flex items-center, this was in the button markup
}
</script>
