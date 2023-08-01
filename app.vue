<template>
  <div class="row">
    <div class="col-1">
      <button class="btn btn-secondary button" @click="add">Add</button>
    </div>

    <div class="col-7">
      <h3>Draggable {{ draggingInfo }}</h3>

      <draggable tag="ul" :list="element" item-key="name" class="list-group" handle=".handle">
        <template #item="{ element }" >
            <li
              class="list-group-item" :key="element.name"
            >
              <span class="handle">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M11 18c0 1.1-.9 2-2 2s-2-.9-2-2 .9-2 2-2 2 .9 2 2zm-2-8c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm0-6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm6 4c1.1 0 2-.9 2-2s-.9-2-2-2-2 .9-2 2 .9 2 2 2zm0 2c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm0 6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"></path></svg>
              </span>
    
              <span class="text">{{ element.name }} </span>
    
              <input type="text" class="form-control" v-model="element.text" />
    
              <i class="fa fa-times close" @click="removeAt(idx)">&times;</i>
            </li>
        </template>
      </draggable>
    </div>
  </div>
</template>

<script>
let id = 3;
import draggable from "vuedraggable";
export default {
  name: "handle",
  display: "Handle",
  instruction: "Drag using the handle icon",
  order: 5,
  components: {
    draggable
  },
  data() {
    return {
      element: [
        { name: "John", text: "", id: 0 },
        { name: "Joao", text: "", id: 1 },
        { name: "Jean", text: "", id: 2 }
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
      this.element.splice(idx, 1);
      console.log(this.element)
    },
    add: function() {
      id++;
      this.element.push({ name: "Juan " + id, id, text: "" });
      console.log(this.element)
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
