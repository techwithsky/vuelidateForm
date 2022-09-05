<template>
    <div class="form">
        <form @submit.prevent="submitForm">
            <div class="inp-span">
                <label for="name">Name :</label><br>
                <input type="text" placeholder="Enter Name" v-model="name">
                <span class="invalid" v-if="!$v.name.required && $v.name.$dirty">Name is required</span>
                <span class="invalid" v-if="!$v.name.alpha && $v.name.required && $v.name.$dirty">only type alphabets</span>
                <span class="invalid" v-if="(!$v.name.minLength || !$v.name.maxLength) && $v.name.$dirty">Name must be between {{ $v.name.$params.minLength.min }} and {{ $v.name.$params.maxLength.max }}</span><br>
            </div>
            <div class="inp-span">
                <label for="email">Email :</label><br>
                <input type="email" placeholder="Enter Email Id" v-model="email">
                <span class="invalid" v-if="!$v.email.required && $v.email.$dirty">Email is required</span>
                <span class="invalid" v-if="!$v.email.email && $v.email.$dirty">Invalid email ID</span>
                <span class="valid" v-if="$v.email.email && $v.email.required && $v.email.$dirty">valid email ID</span><br>

            </div>
            <div class="inp-span">
                <label for="password">Password :</label><br>
                <input type="password" placeholder="Enter Password" v-model="password">
                <span class="invalid" v-if="!$v.password.required && $v.password.$dirty">Password is required</span>
                <span class="invalid" v-if="(!$v.password.minLength || !$v.password.maxLength) && $v.password.$dirty">Password length must be between {{ $v.password.$params.minLength.min }} and {{ $v.password.$params.maxLength.max }}</span>
                <span class="valid" v-if="$v.password.minLength && $v.password.required && $v.password.maxLength && $v.password.$dirty">Valid Password</span><br>
                <!-- <span v-if="(!$v.name.minLength || !$v.name.maxLength) && $v.name.$dirty">Name must be between {{$v.name.$params.minLength.min}} and {{$v.name.$params.maxLength.max}}</span><br> -->

            </div>
            <button type="submit">Submit</button>
        </form>
    </div>
</template>

<script>
import {
    required,
    minLength, alpha, maxLength, email
} from "vuelidate/lib/validators"
export default {
    name: 'vuelidateForm',
    data() {
        return {
            name: '',
            email: '',
            password: ''
        }
    },
    validations: {
        name: {
            required,
            minLength: minLength(3),
            maxLength: maxLength(10),
            alpha
        },
        email: {
            required,
            email
        },
        password: {
            required,
            minLength: minLength(8),
            maxLength: maxLength(20)
        }
    },
    methods: {
        submitForm() {
            this.$v.$touch();
            if (!this.$v.$invalid) {
                console.log(`Name : ${this.name} Email: ${this.email}`)
            }
        }
    }
}
</script>

<style scoped>
.form {
    width: 40%;
    margin-left: auto;
    margin-right: auto;
}
form {
    width: 100%;
}

label {
    float: left;
    margin: 4px 0px;
}

input {
    margin: 10px 0px;
}

span {
    font-size: 16px;
}

.valid {
    color: green
}

.invalid {
    color: rgb(199, 15, 15);
}
</style>>

