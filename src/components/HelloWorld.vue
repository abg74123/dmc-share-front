<template>
  <button>แชร์เลย!!!!!!!!</button>
</template>

<script setup>

import {onMounted} from "vue";
import {liff} from "@line/liff";

 onMounted(async () => {
 console.log("mount")
    try {
      // * Config Line Liff
      await liff.init({ liffId: "2006835240-LbMy0qgq", withLoginOnExternalBrowser: true })
      // ^ Check Line Liff Login ?
      if (liff.isLoggedIn()) {
        const profile = await liff.getProfile()
        console.log("profile => ", profile)
           await liff.sendMessages([{
    "type": "text",
    "text": "Hello, world"
}])
        this.loading = false
      } else {
        liff.login()
      }
    } catch (e) {
      console.log("error login => ", e)

    }
})

</script>