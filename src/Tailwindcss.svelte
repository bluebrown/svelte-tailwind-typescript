<style type="text/postcss" global>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
  body {
    @apply bg-gray-200 h-screen w-screen min-h-0 min-w-0 antialiased;
  }
  input:focus,
  textarea:focus,
  button:focus {
    @apply outline-none shadow-outline;
  }
</style>