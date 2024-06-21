<template>
<div class="login-container">
    <div class="login-box">
        <img src="../assets/img/pages/yamuna_auth_logo.png" alt="YEIDA Logo" class="logo">
        <h2 class="title">Yamuna Expressway Industrial Development Authority</h2>
        <div class="subtitle">(A Government of Uttar Pradesh Undertaking)</div>
        <div class="p-fluid">
            <div class="p-field">
                <label for="username">E-mail / Mobile number</label>
                <InputText id="username" v-model="username" />
            </div>
            <div class="p-field">
                <label for="password">Password</label>
                <Password id="password" v-model="password" feedback="false" />
            </div>
            <div class="p-field-checkbox">
                <Checkbox inputId="rememberMe" v-model="rememberMe" />
                <label for="rememberMe">Remember Me</label>
            </div>
            <Button label="Sign In" class="p-button-primary" @click="signIn" />
            <div class="forgot-password">
                <a href="#">Forgot Password?</a>
            </div>
        </div>
    </div>
</div>
</template>

   
  
<script>
import {
    ref
} from 'vue';

export default {
    setup() {
        const username = ref('');
        const password = ref('');
        const rememberMe = ref(false);

        const signIn = () => {
            // Handle sign-in logic here
            console.log('Sign In clicked', {
                username: username.value,
                password: password.value,
                rememberMe: rememberMe.value
            });
        };

        return {
            username,
            password,
            rememberMe,
            signIn,
        };
    },
};
</script>
   
  
<style scoped>
.login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(to bottom, #1e5799 0%, #2989d8 50%, #207cca 75%, #7db9e8 100%);
}

.login-box {
    background: #ffffff;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

.logo {
    width: 250px;
    margin-bottom: 1rem;
}

.title {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
}

.subtitle {
    font-size: 0.9rem;
    margin-bottom: 1.5rem;
}

.forgot-password {
    margin-top: 1rem;
}

.forgot-password a {
    color: #007bff;
    text-decoration: none;
}
</style>
