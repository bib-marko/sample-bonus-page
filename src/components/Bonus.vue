<template>
    <div class="desktop-temp">
        <div class="col-1">
            <img src="/img/bonus/bonus-banner.png" class="details-desktop-img" />

            <div v-if="!IS_DESKTOP" class="desc">
                <p>
                ENJOY EXCITING PROMOS AND WIN AMAZING PRIZES, ONLY AT
                <a href="https://megabet-paradise.com" target="_blank" rel="noopener noreferrer">MEGABET-PARADISE.COM</a>
                </p>
            </div>
            <img  @click="goToSite" v-if="!IS_DESKTOP" src="/img/bonus/mobile-btn.png" class="play-btn" />
        </div>

    <div class="col-2">
        <img v-if="IS_DESKTOP" src="/img/bonus/title.png" class="title-logo" />
        <img v-else src="/img/logo.png" class="logo" />
        <div class="video-wrapper">
            <video 
                ref="videoRef"
                autoplay 
                muted 
                loop 
                playsinline
                webkit-playsinline
                controlslist="nodownload nofullscreen noremoteplayback" 
                disablepictureinpicture 
                class="no-controls"
                >
                <source src="/video/video.mp4" type="video/mp4" />
            </video>
            <div class="controls">
                <img
                v-if="isMuted"
                src="/img/muted.png"
                class="control-btn"
                @click="toggleMute"
                />
                <img
                v-else
                src="/img/play.png"
                class="control-btn"
                @click="toggleMute"
                />
            </div>
        </div>

        <img v-if="!IS_DESKTOP" src="/img/bonus/title.png" class="title-logo" />

        <div v-if="IS_DESKTOP" class="desc">
            <p>
            ENJOY EXCITING PROMOS AND WIN AMAZING PRIZES, ONLY AT
            </p>   <a href="https://megabet-paradise.com" target="_blank" rel="noopener noreferrer">MEGABET-PARADISE.COM</a>
        </div>
        <img  @click="goToSite" v-if="IS_DESKTOP" src="/img/bonus/desktop-btn.png" class="play-btn" />
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useOrientation } from "../service/orientation";

const videoRef = ref<HTMLVideoElement | null>(null);
const isMuted = ref(true);

const ORIENTATION_UTILS = useOrientation();
const IS_DESKTOP = ORIENTATION_UTILS.IS_DESKTOP;

const goToSite = () => {
  window.open("https://megabet-paradise.com", "_blank");
};

const toggleMute = () => {
  if (videoRef.value) {
    videoRef.value.muted = !videoRef.value.muted;
    isMuted.value = videoRef.value.muted;
  }
};

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lilita+One&display=swap');

.desktop-temp {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  gap: 1rem;
  width: 100%;
  box-sizing: border-box;

}

.col-1,
.col-2 {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

.col-2 {
  order: 1;
}
.col-1 {
  order: 2;
}

.details-desktop-img {
    margin-top: -2rem;
    width: 100%;
    max-width: 240px;
    height: auto;
}

.desc {
  margin-bottom: 2em;
}

.title-logo,
.logo,
.play-btn,
.video-wrapper,
.marquee,
.desc {
  width: 100%;
  max-width: 540px;
  height: auto;
}

.logo {
    max-width: 40%;
}

.title-logo {
    margin-top: 1rem;
    max-width: 60%;
}

.play-btn {
  width: 100%;
  max-width: 340px;
  height: auto;
  margin-top: .5rem;
}


.play-btn {
    cursor: pointer;
    filter: drop-shadow(0 0 20px rgba(255, 255, 255, .9));
    animation: bounce 2s infinite;
}

.video-wrapper {
  position: relative;
  aspect-ratio: 16/9;
  border: 7px solid white;
  border-radius: 30px; 
  overflow: hidden;
  max-width: 80%;
}

.video-wrapper video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

a,
.desc {
  font-family: 'Lilita One', sans-serif;
  color: white;
  text-align: center;
  font-size: clamp(14px, 4vmin, 22px);
  line-height: 1.2;
}

.desc p {
  margin: 0;
  padding: 0;
}

a:hover {
    text-decoration: underline;
}


.video-wrapper {
  position: relative;
  aspect-ratio: 16/9;
  border-radius: 30px;
  overflow: hidden;
}

.video-wrapper video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.controls {
  position: absolute;
  bottom: 10px;
  right: 10px;
  display: flex;
  gap: 8px;
}

.control-btn {
  width: 30px;
  height: 30px;
  cursor: pointer;
  transition: transform 0.2s;
}

.control-btn:hover {
  transform: scale(1.1);
}


.no-controls::-webkit-media-controls {
  display: none !important;
  -webkit-appearance: none;
}

.no-controls::-webkit-media-controls-enclosure {
  display: none !important;
}

@keyframes marquee {
  0%   { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-20px); }
  60% { transform: translateY(-10px); }
}

/* 🖥️ DESKTOP MODE */
@media (min-width: 1439px) and (orientation: landscape) {
    .desktop-temp {
        display: grid;
        grid-template-columns: 1fr 1fr;
        align-items: center;
        justify-items: center;
    }

    .details-desktop-img {
        margin-top: -2rem;
        width: 100%;
        max-width: 740px;
        height: auto;
    }

    .col-1 {  margin-right: 5rem;
        order: 2;
        
    }
    .col-2 {
        padding-top: 5em;
        margin-left: 5rem;
        order: 1;
    }

    .logo {
        margin-top: -2rem;
        margin-bottom: 0;
        max-width: 80%;
    }

    .title-logo {
        margin-top: -2rem;
        margin-bottom: 0;
        max-width: 80%;
    }

    .play-btn {
        width: 100%;
        max-width: 540px;
        height: auto;
        margin-bottom: 0;
    }

    .play-btn {
        cursor: pointer;
        width: 70vmin;
        filter: drop-shadow(0 0 20px rgba(255, 255, 255, .9));
    }

    .desc {
        width: 100%;
        max-width: 740px;
        height: auto;
    }

    a,
    .desc {
        font-family: 'Lilita One', sans-serif;
        color: white;
        text-align: center;
        font-size: 4vmin;
        line-height: 1.2;   
        padding: 0.5em 0;  
        width: 680px;
        text-decoration: none;
    }

    a:hover {
        text-decoration: underline;
    }

    .desc p {
        margin: 0 !important;
        padding: 0 !important;
    }
    
     .video-wrapper {
        margin-top: 1em;
        width: 700px;  
        max-width: 95%; 
    }

}


@media (max-width: 1440px) and (orientation: landscape) { 
 .col-1 {
        margin-top: 4rem;
        
    }
     .col-2 {
        margin-top: 4rem;
        
    }
}

</style>
