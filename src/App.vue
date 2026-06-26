<script>
import Navbar from "./components/Navbar.vue";
import Dashboard from "./components/Dashboard.vue";
import Employees from "./components/Employees.vue";
import Payroll from "./components/Payroll.vue";
import LeaveRequests from "./components/LeaveRequests.vue";
import Attendance from "./components/Attendance.vue";

export default {
  components: {
    Navbar,
    Dashboard,
    Employees,
    Payroll,
    LeaveRequests,
    Attendance,
  },
  // Main place where data shared across all components
  data() {
    return {
      currentPage: "dashboard",
      // Dummy employee records used throughout the HR system
      employees: [
        {
          id: 1,
          name: "John Smith",
          department: "Development",
          position: "Front-End Developer",
          email: "john@moderntech.com",
          phone: "0812645671",
          hireDate: "2021-03-15",
          salary: 35000,
          hourlyRate: 218.75,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 2,
          name: "Sarah Johnson",
          department: "Human Resources",
          position: "HR Manager",
          email: "sarah@moderntech.com",
          phone: "0619345672",
          hireDate: "2020-06-12",
          salary: 42000,
          hourlyRate: 262.5,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 3,
          name: "Mike Brown",
          department: "Finance",
          position: "Accountant",
          email: "mike@moderntech.com",
          phone: "0642345673",
          hireDate: "2019-08-20",
          salary: 38000,
          hourlyRate: 237.5,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 4,
          name: "David Wilson",
          department: "Marketing",
          position: "Marketing Manager",
          email: "david@moderntech.com",
          phone: "0762345674",
          hireDate: "2022-01-10",
          salary: 40000,
          hourlyRate: 250.0,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 5,
          name: "Emma Davis",
          department: "Sales",
          position: "Sales Representative",
          email: "emma@moderntech.com",
          phone: "0622345675",
          hireDate: "2021-05-04",
          salary: 32000,
          hourlyRate: 200.0,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 6,
          name: "James Miller",
          department: "Development",
          position: "Backend Developer",
          email: "james@moderntech.com",
          phone: "0792345676",
          hireDate: "2018-09-15",
          salary: 45000,
          hourlyRate: 281.25,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 7,
          name: "Sophia Moore",
          department: "Quality Assurance",
          position: "QA Tester",
          email: "sophia@moderntech.com",
          phone: "0762345677",
          hireDate: "2022-07-01",
          salary: 30000,
          hourlyRate: 187.5,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 8,
          name: "Daniel Taylor",
          department: "Customer Support",
          position: "Support Specialist",
          email: "daniel@moderntech.com",
          phone: "0752345678",
          hireDate: "2021-10-11",
          salary: 28000,
          hourlyRate: 175.0,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 9,
          name: "Olivia Anderson",
          department: "Development",
          position: "Full Stack Developer",
          email: "olivia@moderntech.com",
          phone: "06112345679",
          hireDate: "2019-04-25",
          salary: 48000,
          hourlyRate: 300.0,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 10,
          name: "William Thomas",
          department: "Sales",
          position: "Sales Manager",
          email: "william@moderntech.com",
          phone: "0682345680",
          hireDate: "2018-02-18",
          salary: 45000,
          hourlyRate: 281.25,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 11,
          name: "Ava White",
          department: "Human Resources",
          position: "HR Assistant",
          email: "ava@moderntech.com",
          phone: "06712345681",
          hireDate: "2023-01-05",
          salary: 29000,
          hourlyRate: 181.25,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 12,
          name: "Benjamin Harris",
          department: "Finance",
          position: "Financial Analyst",
          email: "benjamin@moderntech.com",
          phone: "0792345682",
          hireDate: "2020-12-03",
          salary: 41000,
          hourlyRate: 256.25,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 13,
          name: "Charlotte Martin",
          department: "Marketing",
          position: "Content Strategist",
          email: "charlotte@moderntech.com",
          phone: "0892345683",
          hireDate: "2021-09-15",
          salary: 34000,
          hourlyRate: 212.5,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 14,
          name: "Henry Thompson",
          department: "Customer Support",
          position: "Customer Success Agent",
          email: "henry@moderntech.com",
          phone: "0812345684",
          hireDate: "2022-04-22",
          salary: 27000,
          hourlyRate: 168.75,
          hoursWorked: 160,
          status: "Active",
        },
        {
          id: 15,
          name: "Grace Walker",
          department: "Quality Assurance",
          position: "QA Lead",
          email: "grace@moderntech.com",
          phone: "0862345685",
          hireDate: "2019-11-08",
          salary: 43000,
          hourlyRate: 268.75,
          hoursWorked: 160,
          status: "Active",
        },
      ], // Dummy Leave Request Data
      leaveRequests: [
        {
          id: 1,
          employeeName: "John Smith",
          leaveType: "Sick Leave",
          days: 2,
          status: "Pending",
        },

        {
          id: 2,
          employeeName: "Sarah Johnson",
          leaveType: "Annual Leave",
          days: 5,
          status: "Approved",
        },
      ],
      // Dummy Attendance Records
      attendanceRecords: [
        {
          id: 1,
          employeeName: "John Smith",
          status: "Present",
        },
        {
          id: 2,
          employeeName: "Sarah Johnson",
          status: "Absent",
        },
        {
          id: 3,
          employeeName: "Mike Brown",
          status: "Present",
        },
        {
          id: 4,
          employeeName: "David Wilson",
          status: "Present",
        },
        {
          id: 5,
          employeeName: "Emma Davis",
          status: "Absent",
        },
        {
          id: 6,
          employeeName: "James Miller",
          status: "Present",
        },
        {
          id: 7,
          employeeName: "Sophia Moore",
          status: "Present",
        },
        {
          id: 8,
          employeeName: "Daniel Taylor",
          status: "Absent",
        },
        {
          id: 9,
          employeeName: "Olivia Anderson",
          status: "Present",
        },
        {
          id: 10,
          employeeName: "William Thomas",
          status: "Present",
        },
        {
          id: 11,
          employeeName: "Ava White",
          status: "Present",
        },
        {
          id: 12,
          employeeName: "Benjamin Harris",
          status: "Absent",
        },
        {
          id: 13,
          employeeName: "Charlotte Martin",
          status: "Present",
        },
        {
          id: 14,
          employeeName: "Henry Thompson",
          status: "Present",
        },
        {
          id: 15,
          employeeName: "Grace Walker",
          status: "Present",
        },
      ],
    };
  },
  methods: {
    //Adds Employee
    addEmployee(emp) {
      this.employees.push(emp);
    },
    //Removes Employee
    deleteEmployee(id) {
      this.employees = this.employees.filter((e) => e.id !== id);
    },
    //Adds Leave request
    addLeaveRequest(request) {
      this.leaveRequests.push(request);
    },
    //
    updateEmployee(updated) {
      const index = this.employees.findIndex((e) => e.id === updated.id);
      if (index !== -1) {
        this.employees[index] = updated;
        this.employees = [...this.employees]; // triggers Vue reactivity
      }
    },
    //Saves employee and leave request data to LocalStorage
    saveData() {
      try {
        localStorage.setItem("employees", JSON.stringify(this.employees));
        localStorage.setItem(
          "leaveRequests",
          JSON.stringify(this.leaveRequests),
        );
      } catch (error) {
        console.error("Error saving data:", error);
        alert("Could not save data. Try again.");
      }
    },
  },
  //Loads saved data from LocalStorage
  mounted() {
    const savedEmployees = localStorage.getItem("employees");
    const savedLeaves = localStorage.getItem("leaveRequests");

    if (savedEmployees) {
      this.employees = JSON.parse(savedEmployees);
    }

    if (savedLeaves) {
      this.leaveRequests = JSON.parse(savedLeaves);
    }
  },
  //Saves data whenever employees or leave requests change
  watch: {
    employees: {
      deep: true,
      handler() {
        this.saveData();
      },
    },

    leaveRequests: {
      deep: true,
      handler() {
        this.saveData();
      },
    },
  },
};
</script>

<template>
  <Navbar @change-page="currentPage = $event" />
  <!--Dashboard component-->
  <Dashboard
    v-if="currentPage === 'dashboard'"
    :employees="employees"
    :leaveRequests="leaveRequests"
    :attendanceRecords="attendanceRecords"
  />
  <!--Employees component-->
  <Employees
    v-if="currentPage === 'employees'"
    :employees="employees"
    @add-employee="addEmployee"
    @delete-employee="deleteEmployee"
    @update-employee="updateEmployee"
  />

  <!--Payroll component-->
  <Payroll v-if="currentPage === 'payroll'" :employees="employees" />

  <!--Leave Request component-->
  <LeaveRequests
    v-if="currentPage === 'leaveRequests'"
    :leaveRequests="leaveRequests"
    @add-leave-request="addLeaveRequest"
  />

  <!--Attendance component-->
  <Attendance
    v-if="currentPage === 'attendance'"
    :attendanceRecords="attendanceRecords"
  />
</template>
