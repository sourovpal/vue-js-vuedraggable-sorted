<template>
    <div>
        <button class="btn btn-secondary button" @click="add">Add</button>
        <draggable tag="ul" :list="list" class="list-group" handle=".handle">
          <li
              class="list-group-item"
              v-for="(element, idx) in list"
              :key="element.name"
          >
            <i class="fa fa-align-justify handle">Hello</i>
  
            <span class="text">{{ element.name }} </span>
  
            <input type="text" class="form-control" v-model="element.text" />
  
            <i class="fa fa-times close" @click="removeAt(idx)"></i>
          </li>
        </draggable>
        <pre>
            {{ list }}
        </pre>
    </div>
  </template>
  
  <script>
  import { VueDraggableNext } from 'vue-draggable-next';
  let id = 50;
  export default {
    name: "handle",
    display: "Handle",
    instruction: "Drag using the handle icon",
    order: 5,
    components: {
      draggable: VueDraggableNext,
    },
    data() {
      return {
        list: [
          { name: "Navigation", text: "", id: 0 },
          { name: "Contact", text: "", id: 1 },
          { name: "Products", text: "", id: 2 },
        ],
        dragging: false
      };
    },
    computed: {
      draggingInfo() {
        return this.dragging ? "under drag" : "";
      }
    },
    methods: {
      removeAt(idx) {
        this.list.splice(idx, 1);
      },
      add() {
        id++;
        this.list.push({ name: "Navigation 2 " + id, id, text: "" });
      }
    }
  };
  </script>
  <style scoped>
    .button {
      margin-top: 35px;
    }
    .handle {
      float: left;
      padding-top: 8px;
      padding-bottom: 8px;
    }
    .close {
      float: right;
      padding-top: 8px;
      padding-bottom: 8px;
    }
    input {
      display: inline-block;
      width: 50%;
    }
    .text {
      margin: 20px;
    }
  </style>
