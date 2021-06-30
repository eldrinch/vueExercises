<template
  ><div>
    <h1>Local Component</h1>
    <h2>{{ title }}</h2>
    <!-- <button @click="$emit('addclick')">Add</button> -->
    <button @click="$emit('addclick', 1)">Add</button>
    <button @click="addTwo">Add two</button>
    <br />
    <!-- <slot></slot> -->
    <slot name="header"></slot>
    <br />
    <slot name="content"></slot>
  </div>
</template>

<script>
export default {
  //props: ["title"],
  props: {
    title: String, //Posivis tipos de variaveis = Number, Object, Array, Function
  },

  methods: {
    addTwo: function() {
      this.$emit("addclick", 2);
    },
  },
};
</script>

<style></style>
