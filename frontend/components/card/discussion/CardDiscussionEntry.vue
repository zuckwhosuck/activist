<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <div
    class="card-style flex w-full flex-col justify-center space-y-2 px-3 py-4 md:grow md:justify-start md:py-3 lg:px-5"
  >
    <div class="flex items-center space-x-1">
      <!-- Image Logic Not Yet Implemented. For now placeholder image is a circle colored using placeholder colors.-->
      <div class="h-8 w-8 rounded-full bg-distinct-text"></div>
      <div class="flex items-baseline space-x-1">
        <h5 class="pl-2 font-bold">
          {{ discussionEntry.author }}
        </h5>
        <p>{{ $t("i18n.components.card_discussion_entry.on") }}</p>
        <p>
          {{ discussionEntry.date.toLocaleDateString() }}
        </p>
      </div>
    </div>
    <p class="text-lg">
      {{ discussionEntry.content }}
    </p>
    <BtnAction
      class="block"
      :cta="true"
      fontSize="sm"
      :leftIcon="IconMap.ARROW_UP"
      iconSize="1.25em"
      :counter="discussionEntry.votes"
      ariaLabel="i18n.components.card.discussion._global.upvote_discussion_aria_label"
    />
  </div>
</template>

<script setup lang="ts">
import type { DiscussionEntry } from "~/types/content/discussion";

import { IconMap } from "~/types/icon-map";

defineProps<{
  isPrivate?: boolean;
  discussionEntry: DiscussionEntry;
}>();
</script>
