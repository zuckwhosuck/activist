<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <Disclosure v-slot="{ open }" as="div" class="card-style">
    <DisclosureButton class="focus-brand w-full rounded-md px-4 py-2">
      <div
        class="flex gap-3"
        :class="{ 'items-center': !open, 'items-start': open }"
      >
        <div class="text-primary-text">
          <Icon v-if="open" :name="IconMap.CHEVRON_UP" />
          <Icon v-else :name="IconMap.CHEVRON_DOWN" />
        </div>
        <div class="flex-col">
          <div
            class="flex select-text items-center gap-3 text-left text-primary-text"
          >
            <p>{{ faqEntry.question }}</p>
            <IconEdit
              @click.stop="
                useModalHandlers(
                  'ModalEditFaqEntry' + props.faqEntry.id
                ).openModal()
              "
              @keydown.enter="
                useModalHandlers(
                  'ModalEditFaqEntry' + props.faqEntry.id
                ).openModal()
              "
            />
            <ModalEditFaqEntry
              :faqEntry="faqEntry"
              :pageType="props.pageType"
            />
          </div>
          <DisclosurePanel
            class="mt-2 border-t border-section-div py-2 focus-within:border-0"
          >
            <p class="select-text text-left">
              {{ faqEntry.answer }}
            </p>
          </DisclosurePanel>
        </div>
      </div>
    </DisclosureButton>
  </Disclosure>
</template>

<script setup lang="ts">
import { Disclosure, DisclosureButton, DisclosurePanel } from "@headlessui/vue";

import type { FaqEntry } from "~/types/content/faq-entry";

import { IconMap } from "~/types/icon-map";

const props = defineProps<{
  faqEntry: FaqEntry;
  pageType: "organization" | "group" | "event" | "other";
}>();
</script>
