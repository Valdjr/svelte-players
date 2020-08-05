<script>
    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher();

    let player = {
        name: '',
        points: 0
    }

    const onSubmit = (e) => {
        e.preventDefault();
        dispatch('addplayer', player);
        player = {
            name: '',
            points: 0
        }
    }
</script>

<form class="grind-3 card" on:submit={onSubmit}>
    <input type="text" placeholder="Player name" bind:value={player.name}>
    <input type="text" placeholder="Player points" bind:value={player.points}>
    <input type="submit" class="btn btn-primary" value="Add player">
</form>