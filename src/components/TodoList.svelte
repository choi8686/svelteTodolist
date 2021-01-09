<script>
  import TodoItem from "./TodoItem.svelte";

  export let todos;
  export let onHandleCheck;
  export let onHandleRemove;
  export let onHandleModify;
  // todo 배열에서 체크가 되지 않은 아이템들의 갯수를 나타내고, 반응형으로 값이 변한다. 라벨문법
  $: remaining = todos.filter((t) => !t.checked).length;
</script>

<div>
  {#if remaining}
    <p>남은 일이 {remaining}개 남았어요</p>
  {:else}
    <p>남은 일이 없어요</p>
  {/if}
  <br />
  <!-- each 반복문, 그냥 Prop만 넘겨줌 -->
  {#each todos as todo (todo.id)}
    <TodoItem
      todo="{todo}"
      onHandleCheck="{onHandleCheck}"
      onHandleRemove="{onHandleRemove}"
      onHandleModify="{onHandleModify}"
    />
  {/each}
</div>
