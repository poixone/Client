<template>
  <base-dialog v-model="state.window.isShowingCommandPallete">
    <div class="border-2 border-background-200 flexcol gap-2 fixed bg-background-300 z-50 text-text w-128 max-w-full p-2 rounded-8px center">
      <div class="p-2 flexcol gap-4">
        <input ref="commandPalleteInput" v-model="search" class="bg-transparent placeholder-text placeholder-opacity-50 text-lg" placeholder="Quick search...">
        <div class="h-1px bg-background-200 w-full" />
      </div>

      <div class="min-h-72 max-h-72 overflow-hidden overflow-y-scroll">
        <div v-for="category of new Set(filteredCommandPaletteOptions.map(option => option.category))" :key="category" class=" flexcol">
          <p class="opacity-50 mx-4 my-2 capitalize">
            {{ category }}s
          </p>
          <button
            v-for="option of filteredCommandPaletteOptions.filter(option => option.category === category)"
            :key="option.title"
            class="capitalize items-center flex gap-4 p-4 py-3 rounded-6px focus:bg-background-200 hover:bg-background-400 text-left"
            @click="option.onClickHandler && option.onClickHandler(); state.window.isShowingCommandPallete = false;"
          >
            <fluency-icon :icon="option.icon" />
            <span v-html="option.title" />
          </button>
        </div>
      </div>
    </div>
  </base-dialog>
</template>

<script setup lang="ts">
import { onKeyDown } from "@vueuse/core";
import type { Ref } from "vue";
import { computed, ref, watch } from "vue";
import { commandPaletteOptions } from "../services/commandPaletteOptions";
import { isElectron } from "../services/logic";
import { useState } from "/@/app";
import BaseDialog from "/@/components/base/BaseDialog.vue";

const search = ref("");
const state = useState();
const commandPalleteInput = ref() as Ref<HTMLInputElement>;
const focusKeyFilter = [
	"Control",
	"Backspace",
	"q",
	"w",
	"e",
	"r",
	"t",
	"y",
	"u",
	"i",
	"o",
	"p",
	"a",
	"s",
	"d",
	"f",
	"g",
	"h",
	"j",
	"k",
	"l",
	"z",
	"x",
	"c",
	"v",
	"b",
	"n",
	"m",
	"Q",
	"W",
	"E",
	"R",
	"T",
	"Y",
	"U",
	"I",
	"O",
	"P",
	"A",
	"S",
	"D",
	"F",
	"G",
	"H",
	"J",
	"K",
	"L",
	"Z",
	"X",
	"C",
	"V",
	"B",
	"N",
	"M",
	"1",
	"2",
	"3",
	"4",
	"5",
	"6",
	"7",
	"8",
	"9",
];
onKeyDown(focusKeyFilter, () => commandPalleteInput.value.focus());
watch(
	() => state.window.isShowingCommandPallete,
	() => {
		search.value = "";
		setTimeout(() => commandPalleteInput.value && commandPalleteInput.value.focus(), 10);
	},
);

const filteredCommandPaletteOptions = computed(() => {
	let filtered = commandPaletteOptions.value.filter(option => option.title.toLowerCase().includes(search.value.toLowerCase()));
	!isElectron() && (filtered = filtered.filter(option => !option.electronOnly));
	return filtered;
});

</script>
