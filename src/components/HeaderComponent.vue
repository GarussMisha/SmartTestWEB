<template>
  <header class="header no-margin">
    <div class="logo">
      <button @click="goToHome">Logo</button>
    </div>
    <div class="auth-buttons">
      <button v-if="!isAuthenticated" @click="goToLogin">Login</button>
      <button v-if="!isAuthenticated" @click="goToRegister">Register</button>
      <button v-if="isAuthenticated" @click="goToProfile">Profile</button>
      <button v-if="isAuthenticated" @click="goToLogout">Logout</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  props: {
    isAuthenticated: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    goToHome() {
      // Логика для перехода на главную страницу
      this.$router.push("/");
    },
    goToLogin() {
      // Логика для перехода на страницу входа
      this.$emit("login");
    },
    goToRegister() {
      // Логика для перехода на страницу регистрации
      this.$emit("registration");
    },
    goToProfile() {
      // Логика для перехода на страницу профиля
      this.$router.push("/profile");
    },
    goToLogout() {
      // Логика для выхода из системы
      this.$emit("logout");
    }
  }
};
</script>

<style scoped>
* {
  font-family: "Inter", sans-serif;
}

.header {
  display: flex; /* Устанавливает контейнер flex для выравнивания дочерних элементов горизонтально */
  justify-content: space-between; /* Распределяет элементы по краям, с равными отступами между ними */
  align-items: center; /* Выравнивает элементы по вертикали по центру */
  padding: 15px; /* Убирает внутренние отступы */
  background-color: #000000; /* Задает светло-серый цвет фона для шапки */
  border-bottom: 1px solid #046855; /* Добавляет нижнюю границу для визуального разделения */
  margin: 0; /* Убирает внешние отступы вокруг шапки */
  width: 100%; /* Задает ширину шапки на всю ширину страницы */
  height: 60px;
  box-sizing: border-box; /* Учитывает границы и внутренние отступы в общей ширине и высоте элемента */
}

.logo button {
  font-size: 1.5rem; /* Устанавливает размер шрифта для кнопки логотипа */
  font-weight: bold; /* Делает текст кнопки жирным */
  background: none; /* Убирает фоновый цвет у кнопки */
  border: none; /* Убирает границу у кнопки */
  cursor: pointer; /* Задает указатель в виде руки при наведении на кнопку */
  color: #046855;
}

.auth-buttons button {
  margin-left: 10px; /* Добавляет отступ слева между кнопками */
  padding: 8px 16px; /* Задает внутренние отступы для кнопок, делая их больше и удобнее для нажатия */
  background-color: #005646; /* Устанавливает синий цвет фона для кнопок */
  color: #000000; /* Задает белый цвет текста кнопок */
  border: none; /* Убирает границу у кнопок */
  cursor: pointer; /* Задает указатель в виде руки при наведении на кнопку */
  border-radius: 12px; /* Добавляет скругление углов кнопок */
}

.auth-buttons button:hover {
  background-color: #046855; /* Меняет цвет фона кнопки на более темный при наведении */
}
</style>
