<template>
  <button @click="share()">แชร์เลย!!!!!!!!</button>
</template>

<script setup>

import {onMounted} from "vue";
import {liff} from "@line/liff";

 onMounted(async () => {
 console.log("mount")
    try {
      // * Config Line Liff
      await liff.init({ liffId: "2006835240-4exWlE8E", withLoginOnExternalBrowser: true })
      // ^ Check Line Liff Login ?
      if (liff.isLoggedIn()) {
        const profile = await liff.getProfile()
        console.log("profile => ", profile)
      } else {
        liff.login()
      }
    } catch (e) {
      console.log("error login => ", e)
    }
})

function share() {
 console.log("share")
  if (liff.isApiAvailable("shareTargetPicker")) {
     liff.shareTargetPicker([{
      "type": "text",
      "text": "Hello, world"
    }], {
      isMultiple: true,
    }).then().catch(err => alert(err))
  }
}
</script>