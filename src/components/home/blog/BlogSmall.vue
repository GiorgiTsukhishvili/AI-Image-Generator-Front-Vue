<template>
  <RouterLink
    class="flex justify-between items-center flex-col gap-10"
    :to="{ name: 'blog', params: { id: props.blog.id } }"
  >
    <img
      :src="props.blog.image"
      alt="blog image"
      class="h-[300px] w-full object-fit rounded-2xl"
    />
    <div class="flex flex-col items-start self-stretch">
      <ul class="flex flex-wrap items-center gap-2">
        <li
          v-for="tag in props.blog.tags"
          :key="tag.id"
          :style="randColor()"
          class="px-4 py-2 rounded-md flex justify-center items-center"
        >
          {{ tag.name }}
        </li>
      </ul>
      <h2 class="md:text-3xl text-2xl font-bold mt-5">
        {{ props.blog.title }}
      </h2>
      <p class="mt-5 md:text-xl text-gray-500">
        {{ props.blog.description.slice(0, 180) }}...
        <ArrowRightIcon />
      </p>
      <div class="mt-5 flex items-center gap-5 w-full">
        <img
          :src="props.blog.user.image"
          alt="user image"
          class="h-[60px] w-[60px] object-fit rounded-2xl"
        />
        <div class="self-start">
          <h4 class="font-bold md:text-xl">By : {{ props.blog.user.name }}</h4>
          <p class="text-gray-500">
            {{ calculateData(props.blog.created_at) }}
          </p>
        </div>
      </div>
      <div class="flex gap-4 items-center mt-5">
        <span class="flex gap-2 items-center text-xl">
          <LikeIcon /> {{ props.blog.likes_count }}
        </span>
        <span class="flex gap-2 items-center text-xl">
          <CommentIcon /> {{ props.blog.comments_count }}
        </span>
      </div>
    </div>
  </RouterLink>
</template>

<script setup>
import { ArrowRightIcon, LikeIcon, CommentIcon } from "@/components";
import { RouterLink } from "vue-router";
import { calculateData, randColor } from "@/helpers";

const props = defineProps({
  blog: { type: Object, required: true },
});
</script>
