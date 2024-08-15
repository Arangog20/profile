
<template>
    <nav class="navbar">
      <div class="search-bar">
        <span class="search-icon">🔍</span>
        <input 
          class="inp"
          type="text"
          placeholder="Search"/>
        <span class="shortcut">⌘K</span>
      </div>
      <div class="nav-icons">
        <span class="icon"><i class="fa-solid fa-globe"></i></span>
        <span class="icon"><i class="fa-regular fa-sun"></i></span>
        <span class="icon"><i class="fa-solid fa-box"></i></span>
        <span class="icon"><i class="fa-regular fa-bell"></i></span>
        <div class="profile">
          <img src="https://img.freepik.com/psd-gratis/3d-ilustracion-persona-gafas-sol_23-2149436188.jpg" alt="Profile Picture">
        </div>
      </div>
    </nav>
  </template>

  <script setup lang="ts">
</script>

<style  lang="scss">

body {
  margin: 0;
  font-family: Arial, sans-serif;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 16px;
  background-color: #f5f5f5;
  box-shadow: 0 5px 6px rgba(0, 0, 0, 0.15);
}

.search-bar {
  display: flex;
  align-items: center;
  background-color: white;
  border-radius: 20px;
  padding: 4px 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  
  
 .inp {
    border: none;
    outline: none;
    margin-left: 8px;
    font-size: 14px;
  }

  .shortcut {
    margin-left: auto;
    background-color: #e0e0e0;
    border-radius: 5px;
    padding: 2px 6px;
    font-size: 12px;
    color: #666;
  }

  .search-icon {
    color: #666;
    font-size: 14px;
  }
}

.nav-icons {
  display: flex;
  align-items: center;

  img{
    width: 100%;
    height: 100%;
  }

  .icon {
    margin: 0 8px;
    font-size: 18px;
  }

  .profile {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    overflow: hidden;
    margin-left: 16px;

    img {
      width: 100%;
      height: 100%;
    }
  }
}
</style>