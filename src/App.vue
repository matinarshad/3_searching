<template>
  <div class="col-lg-8 mx-auto p-3 py-md-5">
    <header class="d-flex align-items-center pb-3 mb-5 border-bottom">
      <a
        href="/"
        class="d-flex align-items-center text-dark text-decoration-none"
      >
        <span class="fs-4">📚 SingleView Task 3: Searching</span>
      </a>
    </header>

    <main>
      <h1>Active Members</h1>
      <p class="fs-5">
        Below is a table that contains a generated list of active members. The
        task is to be able to search the members based on the input below.
      </p>

      <br />

      <div class="row g-5">
        <div class="container">
          <div class="row">
            <div class="container">
              <div class="row">
                <div class="col-sm-4 mb-4">
                  <input
                    v-model="search"
                    type="text"
                    class="form-control"
                    id="firstName"
                    placeholder="Search users..."
                    required=""
                  />
                </div>
                <div class="col-sm-8 mb-4 text-end">
                  Displaying {{ computedUsers.length }} users
                </div>
              </div>
            </div>
          </div>
          <div class="row">
            <div v-for="user in computedUsers" :key="user.id" class="col-3">
              <Card :user="user" />
            </div>
          </div>
        </div>
      </div>
    </main>
    <footer class="pt-5 my-5 text-muted border-top">SingleView</footer>
  </div>
</template>

<script>
import Users from "../example_data/data.json";
import Card from "../src/components/Card";

export default {
  name: "App",
  components: {
    Card,
  },
  data() {
    return {
      search: "",
    };
  },
  computed: {
    computedUsers() {
      if (this.search == "") {
        return Users;
      } else {
        return Users.filter(
          (user) =>
            user.first_name.toLowerCase().includes(this.search.toLowerCase()) ||
            user.last_name.toLowerCase().includes(this.search.toLowerCase()) ||
            user.location.toLowerCase().includes(this.search.toLowerCase())
        );
      }

      //return Users;
    },
  },
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.css";
</style>
