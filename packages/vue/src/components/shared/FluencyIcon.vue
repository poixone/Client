<template>
  <div class="icon flex items-center">
    <i-fluency-active-state v-if="icon === 'active-state'" />
    <i-fluency-at-sign v-if="icon === 'at-sign'" />
    <i-fluency-clock v-if="icon === 'clock'" />
    <i-fluency-close v-if="icon === 'close'" />
    <i-fluency-computer v-if="icon === 'computer'" />
    <i-fluency-country v-if="icon === 'country'" />
    <i-fluency-done v-if="icon === 'done'" />
    <i-fluency-down v-if="icon === 'down'" />
    <i-fluency-github v-if="icon === 'github'" />
    <i-fluency-happy-skull v-if="icon === 'happy-skull'" />
    <i-fluency-ipv6 v-if="icon === 'ipv6'" />
    <i-fluency-lightning-bolt v-if="icon === 'lightning-bolt'" />
    <i-fluency-logs v-if="icon === 'logs'" />
    <i-fluency-maximize v-if="icon === 'maximize'" />
    <i-fluency-memory v-if="icon === 'memory'" />
    <i-fluency-minimize v-if="icon === 'minimize'" />
    <i-fluency-nas v-if="icon === 'nas'" />
    <i-fluency-notes v-if="icon === 'notes'" />
    <i-fluency-ping v-if="icon === 'ping'" />
    <i-fluency-pirate-bay v-if="icon === 'pirate-bay'" />
    <i-fluency-plus v-if="icon === 'plus'" />
    <i-fluency-synchronize v-if="icon === 'synchronize'" />
    <i-fluency-palette v-if="icon === 'palette'" />
    <i-fluency-processes v-if="icon === 'processes'" />
    <i-fluency-processor v-if="icon === 'processor'" />
    <i-fluency-restart v-if="icon === 'restart'" />
    <i-fluency-select-column v-if="icon === 'select-column'" />
    <i-fluency-services v-if="icon === 'services'" />
    <i-fluency-color-palette v-if="icon === 'color-palette'" />
    <i-fluency-command-palette v-if="icon === 'command-palette'" />
    <i-fluency-sound v-if="icon === 'sound'" />
    <i-fluency-settings v-if="icon === 'settings'" />
    <i-fluency-skull v-if="icon === 'skull'" />
    <i-fluency-speedometer v-if="icon === 'speedometer'" />
    <i-fluency-status v-if="icon === 'status'" />
    <i-fluency-switch v-if="icon === 'switch'" />
    <i-fluency-tag v-if="icon === 'tag'" />
    <i-fluency-tasks v-if="icon === 'tasks'" />
    <i-fluency-temperature v-if="icon === 'temperature'" />
    <i-fluency-terminal v-if="icon === 'terminal'" />
    <i-fluency-thor-hammer v-if="icon === 'thor-hammer'" />
    <i-fluency-trash v-if="icon === 'trash'" />
    <i-fluency-unmaximize v-if="icon === 'unmaximize'" />
    <i-fluency-up v-if="icon === 'up'" />
    <i-fluency-upgrade v-if="icon === 'upgrade'" />
    <i-fluency-user v-if="icon === 'user'" />
    <i-fluency-video-card v-if="icon === 'video-card'" />
    <i-fluency-zap v-if="icon === 'zap'" />
  </div>
</template>

<script setup lang="ts">
defineProps<{ icon: string }>();
</script>
