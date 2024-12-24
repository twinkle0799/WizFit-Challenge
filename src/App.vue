<template>
  <div id="app">
    <!-- Main Content Section -->
    <main>
      <SchoolList />
    </main>
  </div>
</template>

<script>
import SchoolList from "./components/SchoolList";

export default {
  name: "App",
  components: {
    SchoolList,
  },
};
</script>

<style>
/* General Styles */
body {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
}

/* App Container */
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* Main Content */
main {
  flex: 1;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
</style>
