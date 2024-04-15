<script>
    import './styles.css';
</script>

<div class="background">
    <slot/>
</div>

<style>
    .background {
        width: 100%;
        height: 100%;
        background: 
            radial-gradient(ellipse, transparent 70%, rgba(24, 47, 40, 0.1) 90%, rgba(24, 47, 40, 0.4) 100%),
            /* radial-gradient(circle at center var(calc(100%+2px)), rgb(146, 180, 79) 20px, rgb(172, 219, 79) 400px, transparent 0%), */
            radial-gradient(circle at center 130%, var(--background-primary) 0%, var(--background-secondary) 145%);
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>