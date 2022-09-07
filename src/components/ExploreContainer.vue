<template>
  <div id="container">
    <strong>{{ name }}</strong>
    <p>Explore <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI Components</a></p>
  <ion-grid> 
    <ion-row>
      <ion-col size-xs="12" >
        <div class="test" >test</div>
        <ion-button color="primary">test</ion-button>
      </ion-col>
      <ion-col size-xs="12">
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

<script lang="ts">
import { defineComponent } from 'vue';
import { IonButton, IonGrid, IonRow, IonCol } from '@ionic/vue';

export default defineComponent({
  name: 'ExploreContainer',
  props: {
    name: String
  },
  components: { IonButton, IonGrid, IonRow, IonCol }
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
  background-color: red;
  height: 100px;
}
</style>
