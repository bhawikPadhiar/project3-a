<template>
    <div class="form-control">
        <p>noidea</p>
        <input type="radio" id="one" @change="addrado" value="One" v-model="rado" />
<label for="one">One</label>

<input type="radio" id="two" @change="addrado" value="Two" v-model="rado" />
<label for="two">Two</label>
    </div>
</template>

<script>
export default{
    props:{
     
        textradio:{
           type:String,
        default:function(){
            return ''
        }
    }
    },
    data(){
        return{
            rado:this.textradio
           // names:this.name
        }
    },
    methods:{
        addrado(){
            this.$emit('addradoo',this.rado)
            //console.warn(this.rado)
        }

    }
}
</script>