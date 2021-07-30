<template>
  <article>
    <p>Example component</p>
    <p>We got them props {{ foo }}</p>
  </article>
</template>

<script>
export default ({
  props: {
    foo: String,
  }
})
</script>
