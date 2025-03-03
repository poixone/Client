<template>
  <div class="flexcol bg">
    <machine-header :machine="machine" />
    <div v-if="machine && machine.ram" class="flexcol gap-2 overflow-hidden overflow-y-visible px-4">
      <machine-processor :machine="machine" />
      <machine-memory-composition :memory="machine.ram" :swap="machine.swap" />
      <div class="grid gap-x-4 grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 w-full">
        <machine-disk v-for="disk of machine.disks" :key="disk.mount" :disk="disk" />
      </div>

      <div class="grid gap-x-4 grid-cols-2 md:grid-cols-3 lg:grid-cols-4 w-full">
        <machine-temp-sensor v-for="(sensor, i) of machine.temps" :key="i" :sensor="sensor" />
      </div>
    </div>
    <div v-else class="bg">
      <base-loading-spinner text="Waiting for data from this machine..." />
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import { useRoute } from "vue-router";
import MachineMemoryComposition from "../../components/MachineView/MachineMemoryComposition.vue";
import { useDiscordManager, useState } from "/@/app";
import BaseLoadingSpinner from "/@/components/base/BaseLoadingSpinner.vue";
import MachineDisk from "/@/components/MachineView/MachineDisk.vue";
import MachineHeader from "/@/components/MachineView/MachineHeader.vue";
import MachineProcessor from "/@/components/MachineView/MachineProcessor.vue";
import MachineTempSensor from "/@/components/MachineView/MachineTempSensor.vue";
import { getMachineOsImageKey } from "/@/services/logic";
const route = useRoute();
const state = useState();
const machineUuid = computed(() => route.params.uuid as string);

const machine = computed(() => {
	const machine = state.machines.get(machineUuid.value);
	if (machine?.name) {
		useDiscordManager().updatePresence({
			state: machine.os_name?.replaceAll("'", ""),
			details: machine.name,
			largeImageKey: machine.os_name ? getMachineOsImageKey(machine.os_name) : "main_logo",
			largeImageText: machine.os_name,
			smallImageKey: "viewing",
			smallImageText: `Viewing ${machine.name}`,
			buttons: [
				{
					label: "See Machine",
					url: `https://xornet.cloud/#/dashboard/machine/${machine.uuid}`,
				},
				{
					label: "GitHub",
					url: "https://github.com/xornet-cloud/",
				},
			],
		});
	}

	return machine;
});
</script>

<style scoped lang="postcss">
.bg {
	@apply w-full h-full bg-black bg-opacity-25;
}
</style>
