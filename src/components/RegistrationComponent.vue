<template>
    <div class="registration-box">
      <h2>Регистрация</h2>
      <form @submit.prevent="handleRegister">
        <div class="input-group">
          <label for="email">Email</label>
          <input type="email" id="email" v-model="email" required />
          <label for="email">ФИО</label>
          <input type="email" id="email" v-model="FIO" required />
        </div>
        <div class="input-group">
          <label for="password">Пароль</label>
          <input type="password" id="password" v-model="password" required />
          <label for="password">Повторите пароль</label>
          <input type="password" id="password" v-model="password" required />
        </div>
        <div class="button-group">
          <button type="submit" class="register-button">Регистрация</button>
          <button type="button" @click="goBack" class="back-button">Назад</button>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: "RegistrationComponent",
    data() {
      return {
        email: '',
        password: '',
      };
    },
    methods: {
      handleRegister() {
        // Логика для регистрации пользователя
        console.log(`Registering with Email: ${this.email}, Password: ${this.password}`);
      },
      goBack() {
        // Логика для возврата назад
        this.$emit('cancel-registration');
      },
    },
  };
  </script>
  
  <style scoped>
    * {
    font-family: "Inter", sans-serif;
  }

  .registration-box {
    background: #2b583870;
    padding: 25px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    width: 300px;
    text-align: center;
  }
  
  .input-group {
    margin-bottom: 45px;
    text-align: left;
  }
  
  .input-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
    color: #000000;
  }
  
  .input-group input {
    width: calc(100% - 15px);
    padding: 8px;
    border: 1px solid #005646;
    border-radius: 12px;
  }
  
  .button-group {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }
  
  .register-button {
    padding: 10px 20px;
    background-color: #005646;
    color: #000000;
    border: none;
    cursor: pointer;
    border-radius: 12px;
  }
  
  .back-button {
    padding: 10px 20px;
    background-color: #005646;
    color: #000000;
    border: none;
    cursor: pointer;
    border-radius: 12px;
  }
  
  .register-button:hover {
    background-color: #046855;
  }
  
  .back-button:hover {
    background-color: #046855;
  }
  </style>
  