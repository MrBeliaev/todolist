<template>
  <the-navbar></the-navbar>
  <div class="container with-nav">
    <router-view></router-view>
  </div>
</template>

<script>
import TheNavbar from './components/TheNavbar'

export default {
  components: {
    TheNavbar
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 16px;
    background: rgb(0, 0, 0);
}

a {
    text-decoration: none;
}

.container {
    margin: 0 auto;
    max-width: 1000px;
}

.container.with-nav {
    margin-top: 70px;
}

.btn {
    color: rgb(0, 222, 0);
    position: relative;
    place-content: center;
    place-items: center;
    width: fit-content;
    border-radius: 99px;
    border: 1px solid rgb(0, 222, 0);
    text-decoration: none;
    margin-right: 10px;
    padding: 0.5rem 1.5rem;
    background: #fff;
    transition: all 0.22s;
}

.btn:hover {
    cursor: pointer;
    opacity: 0.8;
}

.btn:disabled {
    cursor: not-allowed;
    opacity: 1!important;
    background: rgb(228, 228, 228)!important;
    border-color: rgb(180, 180, 180) !important;
    color: rgb(131, 131, 131) !important;
}

.btn:active {
    box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.3);
}

.btn.primary {
    background: rgb(0, 222, 0);
    color: rgb(255, 255, 255);
}

.btn.danger {
    background: rgb(255, 0, 0);
    color: rgb(255, 255, 255);
    border-color: rgb(255, 0, 0);
}

.btn.warning {
    background: rgb(255, 166, 0);
    color: rgb(255, 255, 255);
    border-color: rgb(255, 166, 0);
}

.card {
    overflow: hidden;
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 10px;
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
    background: rgb(255, 255, 255);
}

.card-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.text-white {
    color: #fff;
}

.text-white.center {
    text-align: center;
}
</style>
