<script lang="ts">
    import { Button, Jumbotron } from "sveltestrap";

    // untuk bisa transfer data antar props, menggunakan export
    export let user = "user";
    export let role = 1;
</script>

<Jumbotron>
    <h1 class="display-3">Hello, {user}</h1>
    <p class="lead">
        This is a simple hero unit, a simple Jumbotron-style component for
        calling extra attention to featured content or information.
    </p>
    <hr class="my-2" />
    <p>
        It uses utility classes for typography and spacing to space content out
        within the larger container.
    </p>


    <!-- melakukan pengkodisian menggunakan #if kondisi, :else if kondisi, ditutup dengan {/if} -->
    {#if role == 1}
    <p class="lead">
        <Button color="danger">Admin Panel</Button>
    </p>
    {:else if role == 2}
    <p class="lead">
        <Button color="success">Member</Button>
    </p>
    {:else}
    <p class="lead">
        <Button color="primary">welcome</Button>
    </p>
    {/if}
</Jumbotron>
