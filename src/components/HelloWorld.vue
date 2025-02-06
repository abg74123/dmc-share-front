<template>
  <button class="btn-share" @click="share()">SHARE <img class="img-icon" src="../assets/Graphicloads-100-Flat-2-Share-2.256.png" alt=""></button>
</template>

<script setup>

import {onMounted} from "vue";
import {liff} from "@line/liff";

 onMounted(async () => {
 console.log("mount")
    try {
      // * Config Line Liff
      await liff.init({ liffId: "2006835556-noawOQEW", withLoginOnExternalBrowser: true})
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

async function share() {
 console.log("share")
     await liff.shareTargetPicker([
       {
         "type": "flex",
         "altText": "this is a flex message",
         "contents": {
  "type": "bubble",
  "hero": {
    "type": "image",
    "url": "https://aiflow-prod-files-blob-0706fed.s3.ap-southeast-1.amazonaws.com/public/upload/2bb685e7-3005-4559-bfac-9623771485bd/051d8bb8-4262-4f55-b2b5-a51b71840221/50777c-1738057025585.jpg",
    "size": "full",
    "aspectRatio": "20:10",
    "aspectMode": "cover",
    "action": {
      "type": "uri",
      "uri": "https://www.doctormek.com/"
    }
  },
  "body": {
    "type": "box",
    "layout": "vertical",
    "spacing": "md",
    "contents": [
      {
        "type": "text",
        "wrap": true,
        "weight": "bold",
        "gravity": "center",
        "size": "lg",
        "text": "คุณได้รับคำแนะนำพิเศษจากเพื่อนของคุณ"
      },
      {
        "type": "box",
        "layout": "vertical",
        "margin": "lg",
        "spacing": "sm",
        "contents": [
          {
            "type": "box",
            "layout": "baseline",
            "spacing": "sm",
            "contents": [
              {
                "type": "text",
                "text": "โดย",
                "color": "#AAAAAA",
                "size": "sm"
              },
              {
                "type": "text",
                "text": "คุณ พงศธร",
                "wrap": true,
                "size": "sm",
                "color": "#666666"
              }
            ]
          },
          {
            "type": "box",
            "layout": "baseline",
            "spacing": "sm",
            "contents": [
              {
                "type": "text",
                "text": "HN",
                "color": "#AAAAAA",
                "size": "sm"
              },
              {
                "type": "text",
                "text": "HN68999",
                "wrap": true,
                "color": "#666666",
                "size": "sm"
              }
            ]
          },
          {
            "type": "box",
            "layout": "baseline",
            "spacing": "sm",
            "contents": [
              {
                "type": "text",
                "text": "วันที่",
                "color": "#AAAAAA",
                "size": "sm"
              },
              {
                "type": "text",
                "text": "31 ม.ค.2568",
                "color": "#666666",
                "size": "sm"
              }
            ]
          }
        ]
      },
      {
        "type": "box",
        "layout": "vertical",
        "margin": "xs",
        "contents": [
          {
            "type": "image",
            "url": "https://aiflow-prod-files-blob-0706fed.s3.ap-southeast-1.amazonaws.com/public/upload/2bb685e7-3005-4559-bfac-9623771485bd/051d8bb8-4262-4f55-b2b5-a51b71840221/821a36-1738058229987.png",
            "aspectMode": "cover",
            "size": "xl",
            "margin": "none"
          },
          {
            "type": "text",
            "text": "กรุณากดลงทะเบียนเพื่อรับสิทธิ",
            "color": "#AAAAAA",
            "wrap": true,
            "margin": "none",
            "size": "xs"
          },
          {
            "type": "separator",
            "margin": "md"
          },
          {
            "type": "button",
            "action": {
              "type": "uri",
              "label": "ติดต่อแอดมินโดยใช้รหัสแนะนำ",
              "uri": "https://line.me/R/oaMessage/%40doctormekclinic/?REFERRAL_PRO%20HN68999"
            },
            "style": "primary",
            "color": "#F2AC00"
          },
          {
            "type": "separator",
            "margin": "md"
          },
          {
            "type": "button",
            "action": {
              "type": "uri",
              "label": "ลงทะเบียนรับคำปรึกษา",
              "uri": "https://appoint.amara-clinic.com/test"
            },
            "style": "primary",
            "color": "#202C74"
          }
        ]
      }
    ]
  }
}
       }
     ], {
      isMultiple: true,
    })
}
</script>


<style>
  .btn-share{
    display: flex;
    gap:15px;
    align-items: center;
    margin: auto;
    cursor: pointer;
    font-size: 30px;
    padding:10px 30px;
    border:0;
    border-radius: 10px;
    color: #FFF;
    background-color: deepskyblue;
          transition-duration: 0.5s;


  }
    .btn-share:hover{
      transition-duration: 0.5s;
    font-size: 35px;
  }
    .img-icon{
      width: 50px;
    }
</style>