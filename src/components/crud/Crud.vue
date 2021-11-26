<template>
  <div>
    <div class="row d-flex justify-content-center">
      <div class="col-md-3">
        <input
          class="form-control m-2"
          type="text"
          placeholder="Default input"
          aria-label="default input example"
          v-model="title"
        />
        <input
          class="form-control m-2"
          type="text"
          placeholder="Default input"
          aria-label="default input example"
          v-model="text"
        />
        <textarea
          rows="5"
          class="form-control m-2"
          type="text"
          placeholder="Default input"
          aria-label="default input example"
          v-model="status"
        />
        <button @click="setAssignment" class="btn btn-primary m-1 mb-5">
          Adicionar Tarefa
        </button>
      </div>
    </div>

    <div class="container">
      <div class="row">
        <div v-for="tarefa in tarefas" :key="tarefa.id" class="col-3 mb-3">
          <Tarefa
            :title="tarefa.title"
            :text="tarefa.text"
            :stats="tarefa.status"
          />
          <button
            class="btn btn-primary m-1"
            @click="updateAssignment(tarefa.id)"
          >
            Atualizar
          </button>
          <button
            class="btn btn-primary m-1"
            @click="deleteAssignment(tarefa.id)"
          >
            Deletar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import config from "../../../config";
import Tarefa from "./Tarefa.vue";
export default {
  components: {
    Tarefa,
  },
  data: () => ({
    title: null,
    text: null,
    status: null,
    id: null,
    tarefas: ["1", "2", "3"],
  }),
  methods: {
    clean(x) {
      /* this.tarefas.splice(this.tarefas.indexOf(x), 1); */

      // to cut out one element via arr.splice(indexToRemove, numberToRemove);
      this.tarefas.splice(this.tarefa.id, 1);
      this.tarefas.filter(function (n) {
        return n;
      });
      console.log(x);
    },
    addLocal() {
      localStorage.setItem("tarefas", this.oneTarefa);
    },

    async listAssignment() {
      axios
        .get(`${config.api.host}:${config.api.port}/tarefas`, {})
        .then(
          (response) => (
            console.log(response.data),
            (this.tarefas = response.data),
            console.log(this.tarefas)
          )
        );
      this.title = "";
      this.text = "";
      this.status = "";
    },
    async deleteAssignment(xid) {
      axios
        .delete(`${config.api.host}:${config.api.port}/tarefas/${xid}`, {})
        .then();
        this.listAssignment()
    },
    setTarefas(res) {
      this.tarefas = res;
      console.log(res);
    },
    setAssignment() {
      axios
        .post(`${config.api.host}:${config.api.port}/tarefas`, {
          title: this.title,
          text: this.text,
          status: this.status,
        })
        .then(
          (response) => (console.log(response.data), this.listAssignment())
        );
    },
    updateAssignment(xid) {
      axios
        .put(`${config.api.host}:${config.api.port}/tarefas/${xid}`, {
          title: this.title,
          text: this.text,
          status: this.status,
        })
        .then(
          (response) => (
            console.log(response.data),
            (this.tarefas = response.data),
            console.log(this.tarefas),
            this.listAssignment()
          )
        );
    },
  },
  beforeMount() {
    this.listAssignment();
  },
};
</script>

<style>
</style>