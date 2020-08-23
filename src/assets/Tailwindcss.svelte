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
  .minor-button {
    @apply text-xs bg-gray-300 px-2 py-1 rounded-sm shadow-sm;
  }
  .minor-button:hover {
    @apply bg-gray-200;
  }
</style>