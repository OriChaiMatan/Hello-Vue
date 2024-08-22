<template>
  <section class="who-watch">
    <h2>Select a User</h2>
    <ul>
      <li
        v-for="(user, index) in users"
        :key="user.id"
        @click="selectUser(user)"
        :class="{ selected: user.id === selectedUserId }"
      >
      <img :src="`https://robohash.org/${user.id}`" alt="RoboHash Image" />
        {{ user.name }}
        <button @click.stop="deleteUser(index)">Delete</button>
      </li>
    </ul>

    <div class="add-new">
      <input
        v-model="newUserName"
        placeholder="Enter new user name"
        @keyup.enter="addUser"
      />
      <button @click="addUser">Add User</button>
    </div>

    <div v-if="selectedUser" class="modal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <h3>{{ selectedUser.name }}</h3>
        <ul>
          <li v-for="(movie, index) in selectedUser.movies" :key="index">
            {{ movie }}
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      users: [
        {
          id: 1,
          name: "John",
          movies: ["Movie A", "Movie B", "Movie C", "Movie D", "Movie E"],
        },
        {
          id: 2,
          name: "Sarah",
          movies: ["Movie F", "Movie G", "Movie H", "Movie I", "Movie J"],
        },
        {
          id: 3,
          name: "Mike",
          movies: ["Movie K", "Movie L", "Movie M", "Movie N", "Movie O"],
        },
      ],
      newUserName: "",
      selectedUserId: null,
    };
  },
  computed: {
    selectedUser() {
      return this.users.find((user) => user.id === this.selectedUserId);
    },
  },
  methods: {
    addUser() {
      if (this.newUserName.trim() === "") return;

      const newUser = {
        id: Date.now(),
        name: this.newUserName.trim(),
        movies: [], // Default empty movie list
      };
      this.users.push(newUser);
      this.newUserName = "";
    },
    deleteUser(index) {
      this.users.splice(index, 1);
      if (this.selectedUserId === this.users[index]?.id) {
        this.selectedUserId = null;
      }
    },
    selectUser(user) {
      this.selectedUserId = user.id;
    },
    closeModal() {
      this.selectedUserId = null;
    },
  },
};
</script>

<style scoped>
.who-watch {
  margin: 0 auto;
  font-family: Arial, sans-serif;
  border-radius: 15px;
  background: #e7b661;
  padding: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
  display: grid; 
  grid-auto-flow: column;
  gap: 10px; 
}

li {
  padding: 10px;
  background-color: #f9f9f9;
  display: grid; 
  cursor: pointer;
  border-radius: 15px;
}

li.selected {
  background-color: #d3e3fd;
  font-weight: bold;
}

li:hover {
  background-color: #f1f1f1;
}

button {
  background-color: #ff4d4d;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #e60000;
}

input {
  padding: 8px;
  margin-top: 10px;
  width: 80%;
  border: 1px solid #ccc;
  border-radius: 5px;
}

h3 {
  margin-top: 20px;
  color: #376ab2;
}

.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 5px;
  text-align: left;
  position: relative;
}

.close {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 20px;
  cursor: pointer;
}

</style>
