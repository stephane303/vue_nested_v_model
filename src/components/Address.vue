<template>
    <div>
        <input name="street" v-model="localAddress.street">
        <input name="city" v-model="localAddress.city">
        <state v-model="localAddress.state" />
        <input name="zip" v-model="localAddress.zip">
    </div>
</template>
<script>
    import State from "./State";
    export default {
        props: {
            value: {
                type: Object,
                required: true
            }
        },
        components: { State },
        computed: {
            localAddress: {
                get() { return this.value },
                set(localAddress) {this.$emit('input', localAddress)}
            }
        }
    }
</script>