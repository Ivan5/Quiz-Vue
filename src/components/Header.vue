<template>
  <div>
    <b-nav>
      <b-nav-item disabled>
        <b>Fancy Quiz App</b>
      </b-nav-item>
      <b-nav-item disabled>
        <b>Counter: {{ numCorrect }} / {{ numTotal }}</b>
      </b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: ["numCorrect", "numTotal"]
};
</script>

<style>
</style>
