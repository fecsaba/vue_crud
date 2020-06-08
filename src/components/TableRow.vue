<template>
  <tr v-if="!isUpdate">
    <th scope="row">{{ index }}</th>
    <td>{{ tableItem.firstName }}</td>
    <td>{{ tableItem.lastName }}</td>
    <td>{{ tableItem.age }}</td>
    <td>
      <button @click="deleteItem(index)" type="button" class="btn btn-danger">
        Delete
      </button>
    </td>
    <td v-if="!isUpdate">
      <button
        @click="isUpdate = !isUpdate"
        type="button"
        class="btn btn-success"
      >
        Update
      </button>
    </td>
    <td v-if="isUpdate">
      <button type="button" class="btn btn-primary">Submit</button>
    </td>
  </tr>
  <tr v-else>
    <th scope="row">{{ index }}</th>
    <td>
      <input type="text" v-model="tableItem.firstName" class="form-control" />
    </td>
    <td>
      <input type="text" v-model="tableItem.lastName" class="form-control" />
    </td>
    <td><input type="number" v-model.number="tableItem.age" class="form-control" /></td>
    <td>
      <button @click="deleteItem(index)" type="button" class="btn btn-danger">
        Delete
      </button>
    </td>
    <td v-if="!isUpdate">
      <button
        @click="isUpdate = !isUpdate"
        type="button"
        class="btn btn-success"
      >
        Update
      </button>
    </td>
    <td v-if="isUpdate">
      <button @click="submit(index)" type="button" class="btn btn-primary" >
        Submit
      </button>
    </td>
  </tr>
  
</template>

<script>
export default {
  name: "TableRow",
  data() {
    return {
      isUpdate: false,
    };
  },
  props: {
    index: Number,
    tableItem: Object,
    tableItems: Array
  },
  methods: {
    deleteItem(id) {
      this.tableItems.splice(id, 1);
    },
    submit(id) {
      this.tableItems[id] = this.tableItem;
      this.isUpdate = false;
    },
    // computed: {
    //   submitButton() {
    //     return this.tableItem.firstName.length > 3 && this.tableItem.lastName.length > 3 && this.tableItem.age > 1
    //   }
    // },
  },
};
</script>
