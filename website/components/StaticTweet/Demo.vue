<script setup lang="ts">
defineProps<{ id: string }>();
</script>

<template>
  <LegoTweet
    v-slot="{ url }"
    :tweet-id="id"
    class="max-w-[550px] bg-white p-4 rounded-xl border"
  >
    <div class="flex justify-between">
      <LegoTweetUser v-slot="{ user }">
        <div class="flex items-center">
          <LegoTweetUserAvatar>
            <span />
          </LegoTweetUserAvatar>
          <div class="ml-3">
            <p class="font-semibold leading-5">
              {{ user.name }}
            </p>
            <p class="text-gray-400">@{{ user.screen_name }}</p>
          </div>
        </div>
      </LegoTweetUser>

      <LegoTweetLink :href="url">
        <Icon name="uil:twitter" class="text-4xl text-blue-300" />
      </LegoTweetLink>
    </div>
    <LegoTweetText
      class="mt-4 text-base md:text-lg"
      link-class="text-blue-500 hover:underline"
    />

    <LegoTweetMedia
      class="mt-2 rounded-xl overflow-hidden border max-h-[290px]"
    />
    <LegoTweetSummaryCard
      v-slot="{ title, description, domain }"
      class="mt-2 border rounded-xl overflow-hidden bg-white hover:bg-gray-100 transition"
    >
      <div class="px-4 py-2 h-full">
        <p class="text-sm text-gray-400">
          {{ domain }}
        </p>
        <p>{{ title }}</p>
        <p class="text-sm text-gray-400">
          {{ description }}
        </p>
      </div>
    </LegoTweetSummaryCard>

    <div class="mt-2 text-gray-400 flex justify-between">
      <LegoTweetCreatedAt />
      <LegoTweetTerms />
    </div>

    <div class="my-2 h-[1px] w-full bg-gray-200" />

    <LegoTweetAction class="text-gray-500 flex space-x-4">
      <LegoTweetActionLove
        v-slot="{ favorite_count }"
        class="group flex items-center font-semibold text-sm space-x-1"
      >
        <LegoTweetActionLoveIcon
          class="text-pink-600 group-hover:bg-pink-100 p-1.5 rounded-full w-8 h-8"
        />
        <span class="group-hover:text-pink-600 group-hover:underline">
          {{ favorite_count }}
        </span>
      </LegoTweetActionLove>

      <LegoTweetActionReply
        class="group flex items-center font-semibold text-sm space-x-1"
      >
        <LegoTweetActionReplyIcon
          class="text-blue-400 group-hover:bg-blue-100 p-1.5 rounded-full w-8 h-8"
        />
        <span class="group-hover:text-blue-400 group-hover:underline">
          Reply
        </span>
      </LegoTweetActionReply>
      <LegoTweetActionCopy
        v-slot="{ copied }"
        class="group flex items-center font-semibold text-sm space-x-1"
      >
        <LegoTweetActionCopyIcon
          class="group-hover:bg-green-100 group-hover:text-green-500 p-1.5 rounded-full w-8 h-8"
        />

        <span class="group-hover:text-green-400 group-hover:underline">
          {{ copied ? "Copied!" : "Copy link" }}
        </span>
      </LegoTweetActionCopy>
    </LegoTweetAction>

    <LegoTweetReplies
      class="py-2 px-4 mt-2 flex justify-center text-sm font-medium text-blue-500 bg-white hover:bg-blue-50 transition rounded-3xl border"
    />
  </LegoTweet>
</template>
