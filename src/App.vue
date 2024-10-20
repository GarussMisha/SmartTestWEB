<template>
  <div id="app">
    <HeaderComponent :isAuthenticated="isAuthenticated" @logout="handleLogout" @registration="showRegistration" @login="showLogin"/>
    <SidebarComponent v-if="isAuthenticated" />
    <div class="wrapper" v-if="isRegistrationActive">
      <RegistrationComponent :isRegistrationActive= "isRegistrationActive"  @cancel-registration="showRegistration"/>
    </div>
    <div class="wrapper" v-if="isLoginActive">
      <LoginComponent @cancel-login="isLoginActive = false" @loginOn="loginOn" />
    </div>
    <!-- Остальной контент приложения -->
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import SidebarComponent from './components/SidebarComponent.vue';
import RegistrationComponent from './components/RegistrationComponent.vue';
import LoginComponent from './components/LoginComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    SidebarComponent,
    RegistrationComponent,
    LoginComponent,
  },
  data() {
    return {
      isAuthenticated: false, // Заменить на true, если пользователь авторизован
      isRegistrationActive: true, // Статус для отображения компонента регистрации
      isLoginActive: false, // Статус для отображения компонента входа
    };
  },
  methods: {
    handleLogout() {
      // Логика выхода из системы
      this.isAuthenticated = !this.isAuthenticated;
    },
    showRegistration() {
      // Показать окно регистрации
      this.isLoginActive = false
      this.isRegistrationActive = !this.isRegistrationActive;
    },
    showLogin() {
      // Показать окно входа
      this.isRegistrationActive  = false
      this.isLoginActive = !this.isLoginActive;
    },
    loginOn(){
      this.isRegistrationActive  = false
      this.isLoginActive = false
      this.isAuthenticated = true
    }
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

.wrapper {
  padding: 100px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
</style>
