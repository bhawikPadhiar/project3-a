<template>
    <div>
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
       type:{
        posts: Array
       }
    },
    data(){
        return{
            rado:false
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