<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script>
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import { defineComponent } from 'vue';
import {getAuth, signInWithEmailAndPassword} from "firebase/auth"
export default defineComponent({
  name: 'App',
  components: {
    IonApp,
    IonRouterOutlet
  },
  created(){
    const auth = getAuth()

    signInWithEmailAndPassword(auth, "ralejandrobm@gmail.com", "alex11").then((userCredential) => {
      const user = userCredential.user

      if(user == null)
      {
            console.log("no autenticado")
      }
      else
      {
          console.log("autenticado correctamente", user)
      }
    })
  }
});
</script>