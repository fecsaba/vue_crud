<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Age</th>
        </tr>
      </thead>
      <tbody>
        <table-row
          v-for="(tableItem, index) in tableItems"
          :key="index + tableItem.firstName"
          :tableItem="tableItem"
          :index="index"
          :tableItems="tableItems"
        ></table-row>
      </tbody>
    </table>
    <div class="row">
      <button
        type="button"
        class="btn btn-dark btn-block"
        data-toggle="modal"
        data-target="#addItemModal"
      >
        Add new Item
      </button>
    </div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="addItemModal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="addItemModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Add new item</h5>
            <button
              type="button"
              class="close"
              data-dismiss="modal"
              aria-label="Close"
            >
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form>
              <div class="form-row">
                <div class="col-md-4 mb-3">
                  <label for="firstName">First name</label>
                  <input
                    v-model="firstName"
                    type="text"
                    class="form-control"
                    id="firstName"
                    value="Mark"
                    required
                  />
                </div>
                <div class="col-md-4 mb-3">
                  <label for="lastName">Last name</label>
                  <input
                    v-model="lastName"
                    type="text"
                    class="form-control"
                    id="lastName"
                    value="Otto"
                    required
                  />
                </div>
                <div class="col-md-4 mb-3">
                  <label for="age">Age</label>
                  <input
                    v-model="age"
                    type="number"
                    class="form-control"
                    id="age"
                    value="30"
                    required
                  />
                </div>
              </div>
              
              
            </form>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-dismiss="modal"
            >
              Close
            </button>
            <button @click="addItem" type="button" class="btn btn-primary">Save changes</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TableRow from "@/components/TableRow";
export default {
  name: "Table",
  data() {
    return {
      tableItems: [
        {
          firstName: "Mark",
          lastName: "Otto",
          age: 22,
        },
        {
          firstName: "Jacob",
          lastName: "Thornton",
          age: 44,
        },
        {
          firstName: "Larry",
          lastName: "the Bird",
          age: 77,
        },
      ],
      firstName: "",
      lastName: "",
      age: null
    };
  },
  components: {
    TableRow,
  },
  methods: {
    addItem() {
      this.tableItems.push({
        firstName: this.firstName,
        lastName: this.lastName,
        age: this.age,
      });
    },
  },
};
</script>
