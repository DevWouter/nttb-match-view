<style>
    .container {
        background-color: rgb(240, 240,240);
        display: grid;
        grid-template-columns: 90px 1fr 40px 40px;
        grid-template-areas:
            "set title  match-score match-score"
            "p1name p1name p1gamescore p1setscore"
            "p2name p2name p2gamescore p2setscore";
        border: 2px solid var(--nttb-blue);
        font-variant-numeric: tabular-nums;
    }
    .container > * {
        padding: 4px;
    }

    .header {
        background-color: var(--nttb-orange);
        color: white;
        font-weight: bold;
        font-size: larger;
        border-bottom: 2px solid var(--nttb-blue);
    }

    .set {
        grid-area: set;
        padding-right: 20px;
    }

    .title {
        text-align: center;
        grid-area: title;
    }
    .match-score {
        grid-area: match-score;
        padding-left: 20px;
    }
    .player1.name {
        grid-area: p1name;
    }
    .player1.gamescore {
        grid-area: p1gamescore;
    }
    .player1.setscore {
        grid-area: p1setscore;
    }
    .player2.name {
        grid-area: p2name;
    }
    .player2.gamescore {
        grid-area: p2gamescore;
    }
    .player2.setscore {
        grid-area: p2setscore;
    }

    .setscore,
    .gamescore {
        border-left: 2px solid var(--nttb-blue);
    }

    .match-score,
    .gamescore,
    .setscore {
        text-align: center;
    }
</style>

<div class="container">
    <div class="header set">Set 1</div>
    <div class="header title">TTV Ping 1 - TTV Pong 2</div>
    <div class="header match-score">0 - 0</div>
    <div class="player1 name">Ping-3</div>
    <div class="player1 gamescore">1</div>
    <div class="player1 setscore">0</div>
    <div class="player2 name">Pong-8</div>
    <div class="player2 gamescore">1</div>
    <div class="player2 setscore">0</div>
</div>
