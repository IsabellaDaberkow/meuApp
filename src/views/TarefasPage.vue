<template>

  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Tarefas</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tarefas</ion-title>
        </ion-toolbar>
      </ion-header>


     <ion-input label="Digite a Tarefa"  v-model="tarefa">

     </ion-input>

     <ion-button @click="AdicionarTarefa()">
      Adicionar Tarefa
     </ion-button>


    <ion-list>
      <ion-item v-for="(t, index) in tarefas" :key="index">
        {{ t }}

         <ion-button color="danger"  @click="apagarTarefa(index)"> Apagar </ion-button>
      </ion-item>
    </ion-list>

     <p v-if="tarefas.length === 0"> Sem tarefas no momento!</p>

 </ion-content>
 </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, IonInput, IonList, IonItem } from '@ionic/vue';

import { ref } from 'vue' 
const tarefa = ref("")
const tarefas = ref<string[]>([])


function apagarTarefa(index:number) {
  tarefas.value.splice(index, 1)
}

function AdicionarTarefa() {
  if (tarefa.value.trim() === "") return

  tarefas.value.push(tarefa.value)
  tarefa.value = ""
}




</script>

<style scoped >

</style>