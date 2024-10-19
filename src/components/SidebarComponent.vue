<template>
    <aside class="sidebar" :class="{ collapsed: isCollapsed }">
      <button class="toggle-button" @click="toggleSidebar">
        {{ isCollapsed ? '>' : '<<<' }}
      </button>
      <div class="menu" v-if="!isCollapsed">
        <button @click="handleClick('projects')">Проекты</button>
        <button @click="handleClick('profile')">Профиль</button>
        <button @click="handleClick('profile')">pass</button>
        <button @click="handleClick('logout')">pass</button>
      </div>
    </aside>
  </template>
  
  <script>
  export default {
    name: "SidebarComponent",
    data() {
      return {
        isCollapsed: false,
      };
    },
    methods: {
      toggleSidebar() {
        this.isCollapsed = !this.isCollapsed;
      },
      handleClick(action) {
        // Здесь можно добавить обработку кликов по кнопкам меню
        console.log(`Clicked on: ${action}`);
      }
    }
  };
  </script>
  
  <style scoped>
  * {
    font-family: "Inter", sans-serif;
  }

  .sidebar {
    position: fixed;
    top: 59px; /* Высота шапки, чтобы меню начиналось под Header */
    left: 0;
    width: 150px;
    height: calc(100% - 60px); /* До самого низа, учитывая высоту шапки */
    background-color: #046855;
    color: #010101;
    border-bottom: 1px solid #000000;
    border-right: 2px solid #000000;

    transition: width 0.3s ease;
    box-sizing: border-box;
    padding: 10px;
  }
  
  .collapsed {
    width: 50px; /* Уменьшенная ширина при свернутом состоянии */
  }
  
  .toggle-button {
    background: none;
    border: none;
    color: #000000;
    cursor: pointer;
    font-size: 1.2rem;
    margin-bottom: 20px;
  }
  
  .menu button {
    display: block;
    width: 100%;
    background: none;
    border: none;
    color: #000000;
    padding: 10px;
    text-align: left;
    cursor: pointer;
    margin-bottom: 10px;
  }
  
  .menu button:hover {
    background-color: #00000020;
    border-radius: 12px;
  }
  </style>
  