<script>
import Message from "@/components/Message.vue";

export default {
    components:{
        Message
    },
    data(){
        return {
            conversations: [],
            nameUser: '',
            idUser: '',
            mes: '',
        }
    },
    props: {
        name: String,
        id: String,
        name2: String,
        id2: String
    },
    created() {
        if (this.nameUser === '') {
            this.nameUser = this.name
            this.idUser = this.id
        }
    },
    methods:{
        ChangeUser () {
            if (this.nameUser === this.name) {
                this.nameUser = this.name2
                this.idUser = this.id2
            } else {
                this.nameUser = this.name
                this.idUser = this.id
            }
        },
        addData (){
            this.conversations.push({
                mes: this.mes,
                nameSender: this.nameUser
            })
        }
    },

}
  // import {computed, ref} from "vue";
  // import Message from "@/components/Message.vue";
  // const conversations = ref([]);
  // const props = defineProps({
  //     name: String,
  //     id: String,
  //     name2: String,
  //     id2: String
  // })
  // const {name, id, name2, id2} = props
  // const mes = ref("")
  // const nameUser = ref("")
  // const idUser = ref("")
  //
  // nameUser.value = name
  // idUser.value = id
  // const addData = ()=>{
  //     conversations.value.push({
  //         mes: mes,
  //         nameSender: nameUser
  //     })
  // }
  // const ChangeUser = ()=>{
  //     if (nameUser.value === name){
  //         nameUser.value = name2
  //         idUser.value = id2
  //     }else {
  //         nameUser.value = name
  //         idUser.value = id
  //     }
  // }
</script>

<template>
  <div class="bg-white rounded-xl w-96 h-[40rem] overflow-hidden relative pb-32">
    <div class="flex items-center justify-between bg-gray-200 p-3">
        <div class="flex gap-2">
            <img src="../assets/1.jpg" class="w-10 rounded-full" alt="">
            <div>
                <h3 class="text-black font-bold">{{ nameUser }}</h3>
                <p class="text-xs text-gray-500">{{ idUser }}</p>
            </div>
        </div>
        <button type="submit" class="text-red-400" @click="ChangeUser">Change User</button>
    </div>
      <div class="flex w-full absolute z-10 bottom-0 p-3">
          <div class="flex w-full z-10 px-3 rounded-xl bg-gray-200 shadow-xl items-center">
              <input @keyup.enter="addData" v-model="mes" type="text" class="text-blue-800 bg-gray-200 h-12 outline-0 w-full" placeholder="Enter your message">
              <img @click="addData" src="../assets/send.png" alt="" class="w-8 h-6 cursor-pointer">
          </div>
      </div>
      <Message :conversations="conversations"/>

  </div>
</template>

