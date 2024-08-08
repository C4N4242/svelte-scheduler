<script>
  let tasks = []
  let newTask = "";

  function addTask() {
    if (newTask.trim()) {
      tasks = [...tasks, { text: newTask, completed: false }];
      newTask = "";
    }
  }

  function toggleTask(index) {
    tasks[index].completed = !tasks[index].completed;
    tasks = [...tasks];
  }
</script>

<main class="p-4">
  <h1 class="text-2xl font-bold mb-4">予定管理アプリ</h1>
  <input
    type="text"
    bind:value={newTask}
    placeholder="新しいタスクを追加"
    class="border p-2 mb-4 w-full"
  />
  <button on:click={addTask} class="bg-blue-500 text-white p-2">追加</button>

  <ul class="mt-4">
    {#each tasks as task, index}
      <li class="flex items-center mb-2">
        <input type="checkbox" bind:checked={task.completed} on:change={() => toggleTask(index)} />
        <span class="ml-2 {task.completed ? 'line-through' : ''}">{task.text}</span>
      </li>
    {/each}
  </ul>
</main>

<style>
  main {
    max-width: 400px;
    margin: 0 auto;
  }
</style>

