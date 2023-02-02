<template>
    <!-- <div class="container">
        <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal"
            @click="openmodel">
            edit
        </button> -->
    <!-- Modal -->
    <div v-if="OpenClose" class="modal fade show" style="display: block" id="exampleModal" tabindex="-1"
        aria-labelledby="exampleModalLabel">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h1>Edit Title</h1>
                    <h5 class="modal-title" id="exampleModalLabel"></h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" @click="CloseFun"
                        aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <!-- <div>
                           
                            <textcompo ></textcompo>
                            <selectbox />
                            <radiobutton />
                            <checkbox ></checkbox>
                            <textplace/>

                        </div> -->
                    <div>
                        <textcompo :textdata="editlistdata.name" @addnames="textcomp($event)"></textcompo>
                        <selectbox :textlangs="editlistdata.language" @addlangs="selectb($event)" />
                        <radiobutton :textradio="editlistdata.value" @addradoo="radiob($event)" />
                        <checkbox :textos="editlistdata.operatingSystem" @addoss="addos($event)"></checkbox>
                        <textplace :textadd="editlistdata.address" @addaddresses="addresses($event)" />
                    </div>

                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-danger" data-bs-dismiss="modal" @click="CloseFun">
                        Close
                    </button>
                    <button type="button" @click="editDetails(posts)" class="btn btn-primary">
                        Edit Details
                    </button>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
import axios from 'axios'
import checkbox from './CheckBox.vue';
import radiobutton from "./RadioButton.vue"
import selectbox from "./SelectBox.vue"
import textplace from "./TextPlace.vue"
import textcompo from "./TextCompo.vue"
export default {
    props: {
        visible: Boolean,
        postss: Array,
        editlistdata: Object,
        //   variant: String,
    },
    components: {
        checkbox,
        radiobutton,
        selectbox,
        textplace,
        textcompo
    },
    data() {
        return {
            OpenClose: this.visible,
            posts: this.editlistdata,
            name: "",
            address: "",
            operatingSystem: "",
            value: '',
            language: ""
        }
    },
    methods: {
        textcomp(value) {
            this.name = value;
        },
        selectb(value) {
            this.language = value;
        },
        radiob(value) {
            this.value = value;
        },
        addos(value) {
            this.operatingSystem = value;
        },
        addresses(value) {
            this.address = value;
        },
        openmodel() {
            this.OpenClose = !this.OpenClose;

        },
        CloseFun() {
            this.OpenClose = !this.OpenClose;
            this.$emit("close-modal-event");
        },

        async editDetails(posts) {
            console.log(posts)
            await axios.put('http://localhost:3000/postss/' + posts.id,
                {
                    name: this.name == "" ? posts.name : this.name,
                    address: this.address == "" ? posts.address : this.address,
                    operatingSystem: this.operatingSystem == "" ? posts.operatingSystem : this.operatingSystem,
                    value: this.value == "" ? posts.value : this.value,
                    language: this.language == "" ? posts.language : this.language
                }
            ).then(function () {
                window.location.reload()
                //console.log(response);
            })
            this.OpenClose = !this.OpenClose;
            this.$emit("close-modal-event");
        },

    },
    watch: {
        visible: function (newVal) {
            this.OpenClose = newVal;

            //   this.OpenClose = oldVal;
        },
    },
}
</script>