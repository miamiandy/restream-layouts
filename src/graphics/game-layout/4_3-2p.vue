<template>
    <div>
        <!--<twitch-player id="stream1" streamIndex="0"></twitch-player
        <twitch-player id="stream2" streamIndex="1"></twitch-player>-->
        <div id="borderline"></div>
        <div id="fillvoice" class="flexContainer"></div>
        <player-info id="pi1" height="45px" playerIndex="0" :hide-finish-time="true"></player-info>
        <player-info id="pi2" height="45px" playerIndex="1" :hide-finish-time="true"></player-info>
        <div id="timer-and-discord-container" :class="game === 'sms' ? 'SMS' : 'Neutral'">
            <timer-container id="timer"></timer-container>
            <discord-voice-display
                id="discord-voice"
                iconHeight="40px"
                maxUserCount="4"
                nameWidth="125px"
                voice-highlight-color="darkred"
            ></discord-voice-display>
        </div>
        <div v-if="game === 'sms'" id="gameSMS" class="flexContainer">
            <game-container id="gamecSMS"></game-container>
            <img id="logo" src="../../../static/Super_Mario_Sunshine_logo.png" />
        </div>
        <div v-else id="game" class="flexContainer">
            <game-container id="gamec"></game-container>
        </div>
        <bingo-board id="Bingo-board" fontSize="30px"></bingo-board>
        <SubNotifs id="SubNotifsSMS" class="SubNotifs"></SubNotifs>
    </div>
</template>

<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator';
    import { store } from '../../browser-util/state';
    import TimerContainer from '../components/timerContainer.vue';
    import GameContainer from '../components/gameContainer.vue';
    import BingoBoard from '../components/bingoboard.vue';
    import PlayerInfo from '../components/playerInfo.vue';
    import TeamInfo from '../components/teamInfo.vue';
    import PlayerTeamContainer from '../components/playerTeamContainer.vue';
    import DiscordVoiceDisplay from '../components/discordVoiceDisplay.vue';
    import TwitchPlayer from '../components/twitchPlayer.vue';
    import { RunDataTeam } from '../../../speedcontrol-types';
    import SubNotifs from '../components/subNotifs.vue';

    @Component({
        components: {
            BingoBoard,
            GameContainer,
            PlayerInfo,
            TeamInfo,
            PlayerTeamContainer,
            TimerContainer,
            DiscordVoiceDisplay,
            TwitchPlayer,
            SubNotifs
        }
    })
    export default class GameLayout extends Vue {
        get teams(): RunDataTeam[] {
            return store.state.runDataActiveRun.teams;
        }

        get game(): string {
            return store.state.gameMode.game;
        }
    }
</script>

<style scoped>
    #borderline {
        position: absolute;
        top: 0px;
        height: 720px;
        left: 959px;
        width: 2px;
        background: white;
    }

    #discord-voice {
        position: absolute;
        top: 0px;
        left: 0px;
        width: 300px;
        height: 300px;
    }

    #pi1 {
        position: absolute;
        top: 720px;
        left: 0px;
        border: 2px var(--container-border-color) solid;
        width: 665px;
    }

    #pi2 {
        position: absolute;
        top: 720px;
        left: 1240px;
        border: 2px var(--container-border-color) solid;
        width: 665px;
    }

    #Bingo-board {
        position: absolute;
        top: 625px;
        left: 680px;
        opacity: 0.85;
        border: 2px var(--container-border-color) solid;
        width: 560px;
        height: 455px;
    }

    #gameSMS {
        background-image: url('../../../static/background-sunshine.jpg');
        c: cover;
        background-repeat: no-repeat;
        position: absolute;
        top: 780px;
        left: 0px;
        width: 680px;
        border: 2px var(--container-border-color) solid;
        height: 300px;
    }

    #game {
        background-image: url('../../../static/middle-info-background.png');
        background-size: cover;
        background-repeat: no-repeat;
        position: absolute;
        top: 780px;
        left: 0px;
        width: 730px;
        border: 2px var(--container-border-color) solid;
        height: 300px;
    }

    #gamecSMS {
        position: absolute;
        top: 200px;
        left: 0px/*post shift 332px*/;
        width: 680px/*post shift 332px*/;
    }

    #gamec {
        position: absolute;
        top: 100px;
        left: 0px;
        width: 730px;
    }

    #logo {
        position: absolute;
        height: 150px;
        top: 25px;
        left: 233px /*post shift 385px*/ ;
    }

    #timer {
        position: absolute;
        top: 0px;
        left: 250px;
        width: 440px;
        height: 300px;
    }

    #timer-and-discord-container {
        position: absolute;
        left: 1240px;
        top: 780px;
        width: 680px;
        height: 300px;
        border: 2px var(--container-border-color) solid;
    }

    .SMS {
        background-image: url('../../../static/background-sunshine.jpg');
        background-size: cover;
        background-repeat: no-repeat;
    }

    .Neutral {
        background-image: url('../../../static/middle-info-background.png');
    }

    #stream1 {
        position: absolute;
        top: 0px;
        left: 0px;
        width: 960px;
        height: 540px;
        background-image: url('../../../static/middle-info-background.png');
        border: 2px var(--container-border-color) solid;
    }

    #stream2 {
        position: absolute;
        top: 0px;
        left: 960px;
        width: 960px;
        height: 540px;
        background-image: url('../../../static/middle-info-background.png');
        border: 2px var(--container-border-color) solid;
    }

    #discord-voiceBOTW {
        position: absolute;
        top: 600px;
        left: 1190px;
        width: 300px;
        height: 480px;
        border: 2px var(--container-border-color) solid;
        background-image: url('../../../static/middle-info-background.png');
    }

    #discord-voiceNeutral {
        position: absolute;
        top: 780px;
        left: 1192px;
        width: 320px;
        height: 299px;
        border: 2px var(--container-border-color) solid;
        background-image: url('../../../static/middle-info-background.png');
    }

    #pi1BOTW {
        position: absolute;
        top: 540px;
        left: 0px;
        border: 2px var(--container-border-color) solid;
        width: 943px;
    }

    #pi2BOTW {
        position: absolute;
        top: 540px;
        left: 960px;
        border: 2px var(--container-border-color) solid;
        width: 943px;
    }

    #Bingo-boardBOTW {
        position: absolute;
        top: 600px;
        left: 720px;
        border: 2px var(--container-border-color) solid;
        width: 480px;
        height: 480px;
    }

    #gameBOTW {
        background-image: url('../../../static/middle-info-background.png');
        background-size: cover;
        background-repeat: no-repeat;
        position: absolute;
        top: 600px;
        left: 0px;
        width: 730px;
        border: 2px var(--container-border-color) solid;
        height: 480px;
    }

    #gamecBOTW {
        position: absolute;
        top: 270px;
        left: 0px;
        width: 730px;
    }

    #gamecNeutral {
        position: absolute;
        top: 270px;
        left: 0px;
        width: 730px;
    }

    #logoBOTW {
        position: absolute;
        height: 190px;
        top: 70px;
        left: 245px;
    }

    #timerBOTW {
        position: absolute;
        top: 600px;
        left: 1490px;
        width: 440px;
        height: 480px;
        border: 2px var(--container-border-color) solid;
        background-image: url('../../../static/middle-info-background.png');
    }

    #timerNeutral {
        position: absolute;
        top: 600px;
        left: 1490px;
        width: 440px;
        height: 480px;
        border: 2px var(--container-border-color) solid;
        background-image: url('../../../static/middle-info-background.png');
    }

    #Cam1 {
        position: absolute;
        top: 600px;
        left: 398px;
        width: 320px;
        height: 180px;
        background-color: green;
        border: 2px var(--container-border-color) solid;
    }

    #Cam2 {
        position: absolute;
        top: 600px;
        left: 1192px;
        width: 320px;
        height: 180px;
        background-color: green;
        border: 2px var(--container-border-color) solid;
    }

    .SubNotifs {
        position: absolute;
        top: 888px;
        left: 300px;
        height: 200px;
    }

    /*#timer-and-discord-containerBOTW {
    position: absolute;
    left: 1190px;
    top: 600px;
    width: 730px;
    height: 480px;
    background-image: url("../../../static/middle-info-background.png");
    background-size: cover;
    background-repeat: no-repeat;
}*/
</style>
