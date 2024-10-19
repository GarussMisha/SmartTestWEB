<template>
  <div id="app">
    <HeaderComponent />
    <SidebarComponent v-if="isAuthenticated" />
    <div class="registration-wrapper" v-if="isRegistrationActive">
      <RegistrationComponent @cancel-registration="isRegistrationActive = false" />
    </div>
    <!-- Остальной контент приложения -->
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import SidebarComponent from './components/SidebarComponent.vue';
import RegistrationComponent from './components/RegistrationComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    SidebarComponent,
    RegistrationComponent,
  },
  data() {
    return {
      isAuthenticated: true, // Заменить на true, если пользователь авторизован
      isRegistrationActive: false, // Статус для отображения компонента регистрации
    };
  },
};
</script>

<style>
html, body, #app {
  background-color: #00220f15;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  font-family: 'Inter', sans-serif; /* Применяет шрифт ко всему приложению */
}

.registration-wrapper {
  padding: 100px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
</style>
