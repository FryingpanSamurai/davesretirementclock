<!-- two components ? clock and switcher (to switch to seconds/minutes/hours) -->
<script>
    import { onMount } from 'svelte';

    const retirement = new Date("Fri Jun 28 2024 15:00:00 GMT-0600");
    $: today = new Date();
    $: counterMs = retirement - today;
    $: counterDs = Math.floor(counterMs / 100);

    $: seconds = Math.floor((counterMs / 1000) % 60);
    $: minutes = Math.floor((counterMs / (1000 * 60)) % 60);
    $: hours = Math.floor((counterMs / (1000 * 60 * 60)) % 24);
    $: days = Math.floor((counterMs / (1000 * 60 * 60 * 24)));

    const padTime = time => {
      return String(time).length === 1 ? `0${time}` : `${time}`;
    };

    //Return combined values as string in format mm:ss
    $: mydate = `${days}d ${hours}h ${minutes}:${padTime(seconds)}`;

    onMount(() => {
        setInterval(() => {
            counterMs -= 100;
        }, 100);
    })
</script>

<style>
    :global(body) {
        padding: 0;
        margin: 0;
        height: 100vh;
        width: 100vw;
    }

    * {
        font-size: x-large;
    }

    .main-wrapper {
        height: 100%;
        width: 100%;
        /* background-image: linear-gradient(to bottom right, rgb(33,34,41), rgb(42,34,31)); */
        background-color: lavender;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .count-wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 3%;
        text-align: center;
        width: 80%;
        height: 70%;
        min-height: 700px;
        background-color: rgba(11, 11, 11, 0.1);
        border-radius: 15px;
    }

    [class*="row"] {
        width: 97%;
        display: flex;
        align-items: center;
    }

    .f-row {
        flex-direction: column;
        justify-content: center;
        height: 33%;
    }
    
    .s-row {
        justify-content: space-around;
        height: 20%;
        gap: 5%;
    }

    .l-row {
        justify-content: center;
        height: 33%;
    }

    .f-row, .l-row {
        background-color: rgba(11, 11, 11, 0.2);
        border-radius: 10px;
    }

    .hours, .minutes, .miliseconds {
        display: flex;
        flex-direction: column;
    }

    .hours, .minutes {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: rgba(11, 11, 11, 0.2);
        width: 50%;
        height: 100%;
        border-radius: 10px;
    }

    .subtitle, .title {
        font-family: 'Jost', sans-serif;
        color: rgb(144, 111, 104);
        font-size: 28pt;
    }

    .title {
        font-weight: bold;
        font-size: 30pt;
    }

    .sub-text {
        font-family: 'Share Tech Mono', sans-serif;
        font-size: 28pt;
        color: rgba(94, 84, 82);
    }

    @media only screen and (max-width: 768px) {
        * {
            font-size: x-large;
        }

        .main-wrapper {
            height: 100%;
            width: 100%;
            background-image: linear-gradient(to bottom right, rgb(33,34,41), rgb(42,34,31));
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .count-wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            gap: 3%;
            text-align: center;
            width: 88%;
            height: 80%;
            min-height: 700px;
            background-color: rgba(11, 11, 11, 0.1);
            border-radius: 15px;
            padding: 0 10px;
        }

        [class*="row"] {
            width: 97%;
            display: flex;
            align-items: center;
        }

        .f-row {
            flex-direction: column;
            justify-content: center;
            height: 33%;
        }
        
        .s-row {
            justify-content: space-around;
            height: 20%;
            gap: 5%;
        }

        .l-row {
            justify-content: center;
            height: 33%;
        }

        .f-row, .l-row {
            background-color: rgba(11, 11, 11, 0.2);
            border-radius: 10px;
        }

        .hours, .minutes, .miliseconds {
            display: flex;
            flex-direction: column;
        }

        .hours, .minutes {
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: rgba(11, 11, 11, 0.2);
            width: 50%;
            height: 100%;
            border-radius: 10px;
        }

        .subtitle, .title {
            font-family: 'Jost', sans-serif;
            color: rgb(144, 111, 104);
            font-size: 28pt;
        }

        .title {
            font-weight: bold;
            font-size: 30pt;
        }

        .sub-text {
            font-family: 'Share Tech Mono', sans-serif;
            font-size: 28pt;
            color: rgba(94, 84, 82);
        }
    }
</style>

<main class="main-wrapper">
    <!-- clock -->
    <div class="count-wrapper">
        <!-- this will count down to 6/28/2024 @ 3pm -->
        <div class="f-row">
            <span class="title">Dave's Retirement Countdown</span>
            <span class="sub-text">{mydate}</span>
        </div>
        <div class="s-row">
            <section class="hours">
                <span class="subtitle">Hours</span>
                <span class="sub-text">{Math.floor(counterMs / (1000 * 60 * 60))}</span>
            </section>
            <section class="minutes">
                <span class="subtitle">Minutes</span>
                <span class="sub-text">{Math.floor(counterMs / (1000 * 60))}</span>
            </section>
        </div>
        <div class="l-row">
            <section class="miliseconds">
                <span class="subtitle">Seconds</span>
                <span class="sub-text">{Math.floor(counterDs)}</span>
            </section>
        </div>
    </div>
</main>