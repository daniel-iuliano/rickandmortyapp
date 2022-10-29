<script>
    export let character
</script>
<div class="characters">
    <img src={ character.image } alt={ character.name }>
    <h2>{ character.name }</h2>
    
  </div>

  <style>
    h2{
        font-size: 1rem;
        margin: 0 30px 30px 30px;
        height: 30px;
    }
   

    img{
        
        width: 80%;
    }

    .characters{

        background-color: bisque;
        text-align: center;
        border-radius: 10px;
      
    }
  </style>