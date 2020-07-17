<template>
  <q-page class="flex flex-center">
    <div class="column q-gutter-md">
      <div class="row q-gutter-sm">
        <q-btn @click="setVideo(0)" dense label="Set http video"></q-btn>
        <q-btn @click="setVideo(1)" dense label="Set local video"></q-btn>
      </div>
      <div class="row text-red">
        <div v-if="selectedIndex === null">Select a video source first</div>
        <small>
          {{initSource[selectedIndex]}}
        </small>
      </div>
      <div class="row">
        <div class="column items-center">
          <div style="max-width: 640px">
            <q-media-player :sources="sources" @error="onError"></q-media-player>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
/* eslint-disable */
  export default {
    name: 'PageIndex',
    data() {
      return {
        error: null,
        selectedIndex: null,
        initSource: [
          {
            src: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4#t=300',
            type: 'video/mp4'
          },
          {
            src: 'TestVideo.mp4',
            type: 'video/mp4'
          }
        ],
        sources: []
      }
    },
    methods: {
      onError(err) {
        console.log(err);
      },
      setVideo(index) {
        this.selectedIndex = index;
        this.sources = [];
        this.sources.push(this.initSource[index]);
      }
    }
  }
</script>
