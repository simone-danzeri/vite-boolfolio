<script>
import axios from 'axios';
    export default {
        name: 'ContactUs',
        data() {
            return {
                userName: '',
                userEmail: '',
                userMessage: '',
            };
        },
        methods: {
            sendForm() {
                const userData = {
                    name: this.userName,
                    email: this.userEmail,
                    message: this.userMessage
                };
                axios.post('http://127.0.0.1:8000/api/contacts', userData)
                .then((response) => {
                    console.log(response);
                });
            }
        }
    }
</script>

<template>
    <div class="container">
        <div class="text-center my-5">Hi I'm Contact Us</div>
        <form @submit.prevent="sendForm">
            <div class="mb-3">
                <label for="name" class="form-label">Name</label>
                <input type="text" class="form-control" id="name" v-model="userName">
            </div>
            <div class="mb-3">
                <label for="email" class="form-label">Email address</label>
                <input type="email" class="form-control" id="email" v-model="userEmail">
                <small id="emailHelp" class="form-text">We'll never share your email with anyone else.</small>
            </div>
            <div class="mb-3">
                <label for="message" class="form-label">Message</label>
                <textarea class="form-control" id="message" rows="5" v-model="userMessage"></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
    </div>
</template>


<style scoped>

</style>