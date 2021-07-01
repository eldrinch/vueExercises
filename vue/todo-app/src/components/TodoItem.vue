<template>
  <div>
    <InputText v-model="description" />
    <div calss="div-botoes">
      <Button @click="cancel" class="btn-voltar">Voltar</Button>
      <Button @click="saveTodo">Salvar</Button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      description: "",
    };
  },
  props: {
    todo: Object,
  },
  created() {
    if (this.todo) {
      this.description = this.todo.description;
    }
  },
  methods: {
    cancel() {
      this.$emit("cancel");
    },
    saveTodo() {
      this.$emit("saveTodo", { ...this.todo, description: this.description });
    },
  },
};
</script>
<style>
.div-botoes {
  margin-top: 1rem;
}

.btn-voltar {
  margin-right: 1rem;
}
</style>
