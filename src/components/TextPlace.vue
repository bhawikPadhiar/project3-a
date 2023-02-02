<template>
    <div>
        <p>Address</p>

        <input type="text area" class="form-control" placeholder="address" @change="addaddresses" v-model="address" />
    </div>
</template>

<script>
export default {
    props: {
        textadd: {
            type: String,
            default: function () {
                return ''
            }
        }
    },
    data() {
        return {
            address: this.textadd
            // names:this.name
        }
    },
    methods: {
        addaddresses() {
            this.$emit('addaddresses', this.address)
            //console.warn(this.address)
        }

    }
}
</script>