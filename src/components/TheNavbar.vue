<template>
  <nav class="navbar">
    <h3>Список задач</h3>
    <ul class="navbar-menu">
      <li>
        <router-link to="/">Все задачи</router-link>
      </li>
      <li>
        <router-link to="/new">Создать</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {

}
</script>

<style scoped>
  .navbar {
    display: flex;
    padding: 0 2rem;
    justify-content: space-between;
    align-items: center;
    position: fixed;
    z-index: 10;
    top: 0;
    left: 0;
    right: 0;
    height: 4rem;
    background-color: rgb(255, 255, 255);
    box-sizing: border-box;
}

.navbar-menu {
    list-style: none;
    display: flex;
}

.navbar-menu li {
    margin-right: 2rem;
}

.navbar-menu li a {
    color: rgb(0, 0, 0);
    text-decoration: none;
}

.navbar-menu li a:hover, .navbar-menu li a.active {
    border-bottom: 2px solid rgb(0, 222, 0);
}
</style>