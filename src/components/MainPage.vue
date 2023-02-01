<template>
   
    <div class="container">
      <button
        type="button"
        class="btn btn-primary"
        data-bs-toggle="modal"
        data-bs-target="#exampleModal"
        @click="openmodel"
      >
        Mainpage
      </button>
      <!-- Modal -->
      <div
        v-if="OpenClose"
        class="modal fade show"
        style="display: block"
        id="exampleModal"
        tabindex="-1"
        aria-labelledby="exampleModalLabel">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="exampleModalLabel"></h5>
              <button
                type="button"
                class="btn-close"
                data-bs-dismiss="modal"
                @click="CloseFun"
                aria-label="Close"
              ></button>
            </div>
            <div class="modal-body">
    <div>
    
        <textcompo @addnames="textcomp($event)" ></textcompo>
       <selectbox @addlangs="selectb($event)"/>
       <radiobutton @addradoo="radiob($event)"/>
       <checkbox @addoss="addos($event)"></checkbox>      
       <textplace @addaddresses="address($event)"/>

       </div>

            </div>
            <div class="modal-footer">
              <button
                type="button"
                data-bs-dismiss="modal"
                @click="CloseFun"
             
              >
                Close
              </button>
              <button
                type="button"
                @click="saveDetails"
                class="btn btn-primary">
                Save Details
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>  
</template>

<script>
import checkbox from "./CheckBox.vue"
import radiobutton from "./RadioButton.vue"
import selectbox from "./SelectBox.vue"
import textplace from "./TextPlace.vue"
import textcompo from "./TextCompo.vue"
import axios from 'axios'
export default{
    props:{
        visible: Boolean,
   //   variant: String,
    },
    components:{
        checkbox,
        radiobutton,
        selectbox,
        textplace,
        textcompo
    },
    data(){
        return{ 
            OpenClose: this.visible,
            
           postss:{
            name:'',
            addr:'',
            os:'',
            select:'',
            radio:''
           },
           

}
    // main:[]
   
    }, 
    methods:{
        openmodel() {
        this.OpenClose = !this.OpenClose;
        
      },
      CloseFun() {
        this.OpenClose = !this.OpenClose;
        //this.$emit("close-modal-event");
      },
      textcomp(param){
        this.postss.name=param;
       console.log(param)
      },
      selectb(param){
        this.postss.select=param;
      // console.log(param)
      },
      radiob(param){
        this.postss.radio=param;
      //  console.log(param)
      },
      addos(param){
        this.postss.addos=param;
      // console.log(param)
      },
      address(param){
        this.postss.addr=param
       // console.log(param)
      },
     async saveDetails(){
        const res = await axios.post(`http://localhost:3000/postss`, {
        name: this.postss.name,
        address: this.postss.addr,
        operatingSystem: this.postss.addos,
        value: this.postss.radio,
        language:this.postss.select
        // done: false
      });
      console.log(res)
    
    }
      //  console.log(param)
      },
    watch: {
      visible: function (newVal) {
        this.OpenClose = newVal;
        //   this.OpenClose = oldVal;
      },
    },

    }


</script>