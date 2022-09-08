<template>
  <authenticator>
    <template v-slot="{ signOut }">
      <div id="container">
        <strong>{{ name }}</strong>
        <p>Explore <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI
            Components</a></p>
        <ion-grid>
          <ion-row>
            <ion-col size-xs="12" size-sm="6">
              <div class="test">test</div>
              <ion-input placeholder="Enter Input" v-model="taskname"></ion-input>
              <ion-button color="primary" @click="addTask">add</ion-button>
              <ion-button color="primary" @click="signOut">logout</ion-button>
            </ion-col>
            <ion-col size-xs="12" size-sm="6">
              <div>2 of 4</div>
            </ion-col>
            <ion-col size-xs="12">
              <div>3 of 4</div>
            </ion-col>
            <ion-col size-xs="12">
              <div>4 of 4</div>
            </ion-col>
          </ion-row>
        </ion-grid>
      </div>
    </template>
  </authenticator>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { IonButton, IonGrid, IonRow, IonCol, IonInput } from '@ionic/vue';
import { Authenticator } from "@aws-amplify/ui-vue";
import "@aws-amplify/ui-vue/styles.css";
import { API } from 'aws-amplify'
import { createTodo } from '../graphql/mutations'

export default defineComponent({
  name: 'ExploreContainer',
  props: {
    name: String
  },
  components: { IonButton, IonGrid, IonRow, IonCol, Authenticator, IonInput },

  setup() {
    const taskname = ref('')

    const addTask = async () => {
      if (!taskname.value) return
      console.log(taskname.value)
      await API.graphql({
        query: createTodo,
        variables: { input: { "name": taskname.value} }
      })
      taskname.value = ''
    }

    return {
      taskname,
      addTask
    }
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
  /* height: 100% !important; */
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}

.test {
  background-color: rgb(225, 222, 222);
  height: 40px;
}
</style>
