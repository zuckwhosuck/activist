<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <div class="bg-layer-0 px-8">
    <Head>
      <Title>{{ $t("i18n.pages.groups.index.header_title") }}</Title>
    </Head>
    <HeaderAppPage
      :header="$t('i18n.pages.groups.index.header_title')"
      :tagline="$t('i18n.pages.groups.index.subheader')"
    >
      <div class="flex flex-col space-x-3 sm:flex-row">
        <ComboboxTopics />
      </div>
    </HeaderAppPage>
    <div v-if="groups">
      <div v-for="group in groups" class="space-y-6 pb-6 pt-3 md:pt-4">
        <CardSearchResultGroup :isPrivate="false" :group="group" />
      </div>
    </div>
    <EmptyState v-else pageType="groups" :permission="false" />
  </div>
</template>

<script setup lang="ts">
import type { Group } from "~/types/communities/group";

defineProps<{
  groups: Group[];
}>();
</script>
