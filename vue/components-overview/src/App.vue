<template>
  <div>
    <global-component></global-component>
    <local-component :title="title" @addclick="count += $event">
      <!-- Slot Test -->
      <template v-slot:header>
        Slot Header
      </template>
      <template v-slot:content>
        Slot Content
      </template>
    </local-component>
    <p>Count: {{ count }}</p>
  </div>
</template>

<script>
import GlobalComponent from "./components/GlobalComponent.vue";
import LocalComponent from "./components/LocalComponet.vue";

export default {
  data() {
    return {
      title: "Component Title",
      count: 0,
    };
  },

  computed: {
    computedTitle() {
      return "Test " + this.title;
    },
  },

  methods: {},

  components: {
    LocalComponent,
    GlobalComponent,
  },

  //ganchos de inialização HOOKS

  beforeCreate() {
    console.log("beforeCreate", this.title, this.computedTitle);
  },

  created() {
    console.log("created", this.title, this.computedTitle);
  },

  //ganchos de montagem (inserção no DOM)
  beforeMount() {
    console.log("before MOunt");
  },
  mounted() {
    console.log("mounted");
  },

  // ganchos de atualização
  beforeUpdate() {
    console.log("before update");
  },
  updated() {
    console.log("updated");
  },

  // ganchos de destruiçaõ
  beforeUnmount() {
    console.log("beforeUnmount");
  },
  unmounted() {
    console.log("unmounted");
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
