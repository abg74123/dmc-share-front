<template>
  <button>แชร์เลย!!!!!!!!</button>
</template>

<script>

import {onMounted} from "vue";
import {liff} from "@line/liff";

 onMounted(async () => {
 console.log("mount")
    try {
      // * Config Line Liff
      await liff.init({ liffId: "2004029731-Akgo4Bm9", withLoginOnExternalBrowser: true })
      // ^ Check Line Liff Login ?
      if (liff.isLoggedIn()) {
        const profile = await liff.getProfile()
        console.log("profile => ", profile)
        this.loading = false
      } else {
        liff.login()
      }
    } catch (e) {
      console.log("error login => ", e)
    }
})
export default {
  name: 'HelloWorld',
  props: {}
}
</script>