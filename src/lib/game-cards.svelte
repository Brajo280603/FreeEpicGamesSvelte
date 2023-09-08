<script>
    export let gameLink = "";
    export let gameName = "";
    export let gameIcon = "";
    export let gameDesc = "";
  </script>
  
  <a class="flex card card-hover  w-72 sm:h-auto flex-col items-center  antialiased pb-5 overflow-hidden" href="{gameLink}" target="_blank">
    <div class="gameIcon  ">
          <img class="sm:h-auto h-full w-full " src="{gameIcon}" alt="">
      
    </div>
    <div class="flex flex-col mt-3 items-center h-1/4 justify-between">
      <div class="gameName text-lg font-bold">
        <p>{gameName}</p>
      </div>
      <div class="gameDesc font-light text-xs text-center">
        <p>{gameDesc == null?"...":gameDesc}</p>
      </div>
    </div>
  </a>