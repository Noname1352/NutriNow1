<template>
    <div class="register" v-if="!this.islogin">
        <form @submit.prevent="Register">
            <h2>Регистрация</h2>
            <input type="text" placeholder="Имя" v-model="this.name" required>
            <input type="password" placeholder="Пароль" v-model="this.password" required>
            <div class="radiobuttons">
                <label>
                    <input type="radio" name="gender" class="radiobutton" value="Man" v-model="this.gender">
                    <div class="g">Мужчина</div>
                </label>
                <label>
                    <input type="radio" name="gender" class="radiobutton" value="Woman" v-model="this.gender">
                    <div class="g">Женщина</div>
                </label>
            </div>
            <input type="submit" value="Зарегистрироваться">
        </form>
    </div>
    <div v-else class="afterlogin">
        <AfterLogin/>
    </div>
</template>

<script>
import axios from 'axios';
import AfterLogin from './AfterLogin.vue'

export default {
    data() {
        return {
            name: '',
            gender: 'Man',
            password: '',
            islogin: false,
            err: ''
        }
    },
    components: { AfterLogin },
    mounted() {
        if (localStorage.data) {
            this.islogin = true
        }
        else {
            this.islogin = false
        }
    },
    methods: {
        Register() {
            // const request = JSON.stringify({
            //     name: this.name,
            //     gender: this.gender,
            //     password: this.password
            // })
            // axios({
            //     method: 'POST',
            //     url: 'http://localhost:3000/register',
            //     data: request
            // })
            // .then(res => {
            //     if (res.data == 'Аккаунт успешно создан'){
            //         localStorage.data = JSON.stringify({id: this.id, name: this.name, gender: this.gender, password: this.password})
            //         this.islogin = true
            //     }
            //     else {
            //         alert(res.data)
            //     }
            // })

            if (this.name == 'Radik') {
                alert('Аккаунт с текущим именем уже существует')
            }
            else {
                this.islogin = true
                localStorage.data = JSON.stringify({name: this.name, gender: this.gender, password: this.password})
            }
            // let list = JSON.parse(localStorage.users)
            // for (let i of list){
            //     if (i[0] == this.name){
            //         this.err = true
            //     }
            // }
            // if (!this.err) {
            //     this.islogin = true
            //     localStorage.data = [this.name, this.gender, this.password]
            //     list.push([this.name, this.gender, this.password])
            //     localStorage.users = JSON.stringify(list)
            // }
            // else {
            //     alert('Аккаунт с текущим именем уже существует')
            //     this.err = false
            // }
        }
    }
}
</script>

<style scoped>
.register {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 90vh;
    width: 100vw;
    color: white;
}

form {
    background-color: black;
    padding: 20px;
    border-radius: 20px;
}

input {  
    width: 100%;
    padding: 10px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type="submit"] {
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    width: 100%;
}

input[type="submit"]:hover {
    background-color: #45a049;
}

h2 {
    text-align: center;
}

.link {
    color: white;
    text-decoration: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: red;
}

.auth {
    text-align: center;
    width: 100%;
    height: 90%;
}

label {
    display: flex;
    justify-content: space-between;
}

.radiobutton {
    width: 100%;
}

.radiobuttons {
    display: flex;
    justify-content: space-around;
}

.g {
    padding: 10px;
}
</style>