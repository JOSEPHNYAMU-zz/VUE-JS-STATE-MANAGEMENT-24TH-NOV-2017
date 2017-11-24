<template>
    <div id="app">
        <app-registration @userRegistered="userRegistered" :users="unregisteredUsers"></app-registration>
        <app-registrations @userUnregistered="userUnregistered" :registrations="registrations"></app-registrations>
    </div>
</template>

<script>
    import Registration from './components/Registration.vue';
    import Registrations from './components/Registrations.vue';
    export default {
        data() {
            return {
                registrations: [],
                users: [
                    {id: 1, name: 'Joseph Nyamu', registered: false},
                    {id: 2, name: 'James Njoroge', registered: false},
                    {id: 3, name: 'Otieno John', registered: false},
                    {id: 4, name: 'Mary Owiti', registered: false},
                    {id: 5, name: 'Anthony Maina', registered: false}
                ]
            }
        },
        computed: {
            unregisteredUsers() {
                return this.users.filter((user) => {
                    return !user.registered;
                });
            }
        },
        methods: {
            userRegistered(user) {
                const date = new Date;
                this.registrations.push({userId: user.id, name: user.name})
            },
            userUnregistered(registration) {
                const user = this.users.find(user => {
                    return user.id == registration.userId;
                });
                user.registered = false;
                this.registrations.splice(this.registrations.indexOf(registration), 1);
            }
        },
        components: {
            appRegistration: Registration,
            appRegistrations: Registrations
        }
    }
</script>
<style src="./index.css"></style>