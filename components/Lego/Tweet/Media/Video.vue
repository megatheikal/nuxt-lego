<script setup lang="ts">
import type { MediaVideo } from "lego/types";
import { getMediaUrl } from "lego/utils/twitter";

defineProps<{
  media: MediaVideo;
}>();
</script>

<template>
  <video
    v-if="media"
    :poster="getMediaUrl(media, 'small')"
    draggable
    muted
    preload="metadata"
  >
    <source
      :src="media.url"
      :type="media.video_info.variants?.[0].content_type"
    >
  </video>
</template>
