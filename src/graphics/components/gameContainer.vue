<template>
    <div>
        <div v-if="gameMode.game === 'sa2b'" class="GameContainer FlexContainer">
            <div class="GameName FlexContainer">Bingo League</div>
            <div class="GameExtra FlexContainer">{{ gameCategory }}</div>
        </div>
        <div v-else-if="gameMode.game === 'botw'" class="GameContainer FlexContainer">
            <div class="GameName FlexContainer">The Legend of Zelda: Breath of the Wild</div>
            <div class="DivName FlexContainer">{{ gameName }}</div>
            <div class="GameExtra FlexContainer">{{ gameCategory }}</div>
        </div>
        <div v-else class="GameContainer FlexContainer">
            <div class="GameName FlexContainer">{{ gameName }}</div>
            <div class="GameExtra FlexContainer">{{ gameCategory }}</div>
        </div>
    </div>
</template>

<script lang="ts">
    import { Vue, Component } from 'vue-property-decorator';
    import { store } from '../../browser-util/state';
    import { GameMode } from '../../../schemas';
    @Component({})
    export default class GameContainer extends Vue {
        get gameName(): string {
            return store.state.runDataActiveRun.game;
        }
        get gameCategory(): string {
            return store.state.runDataActiveRun.category;
        }
        get gameSystem(): string {
            return store.state.runDataActiveRun.system;
        }
        get gameEstimate(): string {
            return store.state.runDataActiveRun.estimate;
        }

        get gameMode(): GameMode {
            return store.state.gameMode;
        }
    }
</script>

<style>
    .GameContainer {
        align-content: center;
        align-items: center;
        flex-direction: column;
        height: 100%;
    }
    .GameContainer > .GameName {
        font-weight: 500;
        font-size: 30px;
        align-content: center;
        align-items: center;
        color: white;
        text-align: center;
        margin: 5px;
        text-shadow: 3px 3px 5px black;
    }
    .GameContainer > .GameExtra {
        font-size: 20px;
        font-weight: thin;
        align-content: center;
        color: white;
        text-align: center;
        text-shadow: 1px 1px 5px black;
    }

    .GameContainer > .DivName {
        font-size: 25px;
        font-weight: thin;
        align-content: center;
        color: white;
        text-align: center;
        text-shadow: 1px 1px 5px black;
    }
</style>
