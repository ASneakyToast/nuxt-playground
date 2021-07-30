<template>
  <main>
    <p>This is a dyanmyc page</p>
    <p>it has an id of: {{ this.$route.params.id }}</p>
    <NuxtLink to="/">return home</NuxtLink>
  </main>
</template>
