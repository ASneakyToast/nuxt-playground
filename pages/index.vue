<template>
  <main>
    <section>
      <NuxtLink to="/fun">Fun</NuxtLink>
      <NuxtLink to="/p5">p5</NuxtLink>
      <NuxtLink to="/three">three</NuxtLink>
    </section>
    <section>
      <button v-on:click="greet">Greet</button>
    </section>
    <section>
      <h4>Props</h4>
      <ExampleComponent foo="bar!"></ExampleComponent>
    </section>
  </main>
</template>

<script>
export default ({
  data: () => {
    return {
      name: 'joel',
    }
  },
  methods: {
    greet: function (event) {
      alert( 'Hello ' + this.name + '!' );
      console.info( event.target.tagName);
    }
  },
})
</script>
