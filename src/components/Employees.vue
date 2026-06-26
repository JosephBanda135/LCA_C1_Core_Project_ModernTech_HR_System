<script>
export default {
  props: {
    employees: {
      type: Array,
      default: () => [],
    },
  },

  data() {
    return {
      // Stores information into the add employee form
      newEmployee: {
        id: "",
        name: "",
        department: "",
        position: "",
        salary: "",
        hourlyRate: "",
        hoursWorked: 160,
        email: "",
        phone: "",
        hireDate: "",
        status: "Active",
      },
      // Stores the employee currently being edited, null means no edit in progress
      editingEmployee: null,
      // Controls inline feedback message
      message: {
        text: "",
        type: "",
        visible: false,
      },
    };
  },

  methods: {
    // Shows a Bootstrap inline alert then hides it after 3 seconds
    showMessage(text, type) {
      this.message.text = text;
      this.message.type = type;
      this.message.visible = true;

      setTimeout(() => {
        this.message.visible = false;
      }, 3000);
    },

    addEmployee() {
      if (!this.newEmployee.name || !this.newEmployee.department) {
        this.showMessage("Please fill in required fields.", "danger");
        return;
      }

      if (this.newEmployee.salary <= 0) {
        this.showMessage("Salary must be greater than 0.", "danger");
        return;
      }

      this.$emit("add-employee", {
        ...this.newEmployee,
        id: this.employees.length + 1,
        salary: Number(this.newEmployee.salary),
        hourlyRate: Number(this.newEmployee.hourlyRate),
        hoursWorked: Number(this.newEmployee.hoursWorked),
      });

      this.showMessage("Employee added successfully!", "success");

      this.newEmployee = {
        id: "",
        name: "",
        department: "",
        position: "",
        email: "",
        phone: "",
        hireDate: "",
        salary: "",
        hourlyRate: "",
        hoursWorked: 160,
        status: "Active",
      };
    },

    //Deletes Employee
    deleteEmployee(id) {
      this.$emit("delete-employee", id);
      this.showMessage("Employee deleted.", "danger");
    },

    // Loads employee data into the edit form
    startEdit(employee) {
      this.editingEmployee = { ...employee };
    },

    // Saves the edited employee back to App.vue
    saveEdit() {
      this.$emit("update-employee", {
        ...this.editingEmployee,
        salary: Number(this.editingEmployee.salary),
        hourlyRate: Number(this.editingEmployee.hourlyRate),
        hoursWorked: Number(this.editingEmployee.hoursWorked),
      });
      this.editingEmployee = null;
      this.showMessage("Employee updated successfully!", "success");
    },

    // Cancels editing without saving
    cancelEdit() {
      this.editingEmployee = null;
    },
  },
};
</script>

<template>
  <div class="container mt-4">
    <h1 class="text-center mb-4">Employee Management</h1>

    <!-- Inline feedback message -->
    <div
      v-if="message.visible"
      :class="`alert alert-${message.type} alert-dismissible`"
      role="alert"
    >
      {{ message.text }}
      <button
        type="button"
        class="btn-close"
        @click="message.visible = false"
      ></button>
    </div>

    <div class="card shadow p-4 mb-4">
      <h3 class="mb-3">Add Employee</h3>

      <div class="row g-3">
        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="ID"
            v-model="newEmployee.id"
          />
        </div>

        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Name"
            v-model="newEmployee.name"
          />
        </div>

        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Department"
            v-model="newEmployee.department"
          />
        </div>

        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Position"
            v-model="newEmployee.position"
          />
        </div>

        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="Salary"
            v-model="newEmployee.salary"
          />
        </div>

        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="Hourly Rate"
            v-model="newEmployee.hourlyRate"
          />
        </div>

        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="Hours Worked"
            v-model="newEmployee.hoursWorked"
          />
        </div>

        <div class="col-md-2">
          <input
            type="email"
            class="form-control"
            placeholder="Email"
            v-model="newEmployee.email"
          />
        </div>

        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Phone"
            v-model="newEmployee.phone"
          />
        </div>

        <div class="col-md-2">
          <input
            type="date"
            class="form-control"
            placeholder="date"
            v-model="newEmployee.hireDate"
          />
        </div>

        <div class="col-md-2">
          <button class="btn btn-primary w-100" @click="addEmployee">
            Add Employee
          </button>
        </div>
      </div>
    </div>

    <!-- Edit Employee form - only shows when editing -->
    <div class="card shadow p-4 mb-4 border-warning" v-if="editingEmployee">
      <h3 class="mb-3">Edit Employee</h3>
      <div class="row g-3">
        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Name"
            v-model="editingEmployee.name"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Department"
            v-model="editingEmployee.department"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Position"
            v-model="editingEmployee.position"
          />
        </div>
        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="Salary"
            v-model="editingEmployee.salary"
          />
        </div>
        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="Hourly Rate"
            v-model="editingEmployee.hourlyRate"
          />
        </div>
        <div class="col-md-2">
          <input
            type="number"
            class="form-control"
            placeholder="Hours Worked"
            v-model="editingEmployee.hoursWorked"
          />
        </div>
        <div class="col-md-2">
          <input
            type="email"
            class="form-control"
            placeholder="Email"
            v-model="editingEmployee.email"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control"
            placeholder="Phone"
            v-model="editingEmployee.phone"
          />
        </div>
        <div class="col-md-2">
          <button class="btn btn-success w-100" @click="saveEdit">Save</button>
        </div>
        <div class="col-md-2">
          <button class="btn btn-secondary w-100" @click="cancelEdit">
            Cancel
          </button>
        </div>
      </div>
    </div>

    <div class="card shadow p-3">
      <h3 class="mb-3">Employees</h3>

      <div class="table-responsive">
        <table class="table table-striped table-hover table-bordered">
          <thead class="table-dark">
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Department</th>
              <th>Position</th>
              <th>Salary</th>
              <th>Email</th>
              <th>Phone</th>
              <th>Hire Date</th>
              <th>Status</th>
              <th>Action</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="employee in employees" :key="employee.id">
              <td>{{ employee.id }}</td>
              <td>{{ employee.name }}</td>
              <td>{{ employee.department }}</td>
              <td>{{ employee.position }}</td>
              <td>R{{ employee.salary }}</td>
              <td>{{ employee.email }}</td>
              <td>{{ employee.phone }}</td>
              <td>{{ employee.hireDate }}</td>
              <td>
                <span class="badge bg-success">
                  {{ employee.status }}
                </span>
              </td>
              <td>
                <button
                  class="btn btn-warning btn-sm me-2"
                  @click="startEdit(employee)"
                >
                  Edit
                </button>
                <button
                  class="btn btn-danger btn-sm"
                  @click="deleteEmployee(employee.id)"
                >
                  Delete
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
