<template>
    <div style="padding-top:60px;">
        <div class="summary">
            <h3>TOTAL REGISTRATIONS</h3>
            <h5>Total: {{ total }}</h5>
        </div>
        <hr>
        <div class="row" v-for="registration in registrations" style="padding-top:20px;">
            <h4>{{ registration.name }}</h4>
            <span style="background-color: green;padding:10px;margin:12px;color:#ffffff;cursor:pointer;" @click="unregister(registration)">REMOVE</span>
            <div class="date">{{ registration.date }}</div>
        </div>
<div>
        <p>{{ encoded }}</p>
        <p>{{ decoded }}</p>
        <p>{{ error }}</p>
</div>
    </div>
</template>

<script>
    export default {
        props: ['registrations'],
        methods: {
            unregister(registration) {
                this.$emit('userUnregistered', registration);
            }
        },
        computed: {
            total() {
                return this.registrations.length;
            }
        }
    }
</script>
