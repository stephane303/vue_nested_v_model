<template>
    <form>
        <input name="name" v-model="name">
        <input name="email" v-model="email">
        <mailing-address
            :value="address"
            @input="(newAddress) => {address = newAddress}"
        />
        <date-picker  v-model="date"/>
    </form>
</template>
<script>
    import MailingAddress from './Address.vue';
    import DatePicker from './DatePicker.vue';
    export default {
        components: { MailingAddress , DatePicker },
        data() {
            return {
                date: '04-11-2026T2:11 AM',
                name: '',
                email: '',
                address: {
                    street: '',
                    city: '',
                    state: '',
                    zip: ''
                }
            }
        }
    }
</script>