<template>
  <div class="h-screen w-screen box-content m-0 flex flex-wrap overflow-hidden bg-slate-300">
    <PlayerCard v-for="(player, playerIndex) in players" :key="playerIndex" :player="player" />
    <EmptyPlayerCard v-if="players.length < 6" @click="addPlayer" />
    <PlayerNameSelection
      v-if="showPlayerNameSelection"
      @create="createPlayer"
      @exit="showPlayerNameSelection = false"
    />
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue';
import PlayerCard from './components/PlayerCard.vue';
import EmptyPlayerCard from './components/EmptyPlayerCard.vue';
import PlayerNameSelection from './components/PlayerNameSelection.vue';
import { Player } from './types/Player';

const players = reactive([] as Player[]);

const showPlayerNameSelection = ref(false);
const addPlayer = () => {
  showPlayerNameSelection.value = true;
};

const createPlayer = (playerName: string) => {
  players.push({
    name: playerName,
    embers: 0,
    keys: 0,
  });
  showPlayerNameSelection.value = false;
};
</script>

<style scoped></style>
