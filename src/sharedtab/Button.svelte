<script>
  export let btnType = "primary";
  export let flat = false;
  export let invase = false;
  
</script>


<main>
    <button class={btnType} class:flat={flat} class:invase={invase}>
        <slot></slot>
      </button>
</main>


<style>

    button{
        width: 100%;
        cursor: pointer;
        border-radius: 6px;
        padding: 8px 12px;
        box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
    }
 .primary{
    background-color: #ff0000e8;
    color: white;
 }

 .secondary{
    background-color: green;
    color: white;
 }

 .primary.invase{
    color: #ff0000;
    background-color:#ffffff ;
    border: 2px  solid #ff0000;
 }


 .secondary.invase{
    color: #008000;
    background-color:#ffffff ;
    border: 2px  solid #008000;
 }
</style>