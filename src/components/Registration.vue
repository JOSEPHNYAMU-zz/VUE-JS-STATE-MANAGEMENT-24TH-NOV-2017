<template>
    <div class="dashboard" style="margin-top:35px;">
        <fieldset><legend>CLICK TO ADD USERS</legend>
        <div class="row" v-for="user in users">
            <h4>{{ user.name }}</h4>
            <button class="btn" @click="registerUser(user)">Register</button>
        </div>
        </fieldset>
    </div>
</template>

<script>
    export default {
        props: ['users'],
        methods: {
            registerUser(user) {
                this.$emit('userRegistered', user);
                user.registered = true;
            }
        }
    }
</script>
