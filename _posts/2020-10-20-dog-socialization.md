---
title: "Dog Socialization Sounds" 
excerpt: "Playlist of sounds to help socialize your canine"
classes: wide
categories:
  - other
tags:
  - dog
permalink: /dog-socialization/
title: "Dog Socialization Sounds"
---
<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/amplitudejs@v5.2.0/dist/amplitude.js"></script>
<script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>

<style>
  div#amplitude-player {
    background: #FFFFFF;
    box-shadow: 0 2px 12px 8px rgba(0, 0, 0, 0.1);
    margin: auto;
    margin-top: 20px;
    margin-bottom: 20px;
    display: flex;
    max-width: 900px; }

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    div#amplitude-player {
      flex-direction: column; } }
  /* Medium only */
  @media screen and (min-width: 40em) and (max-width: 63.9375em) {
    div#amplitude-player {
      max-height: 715px; } }
  /* Large and up */
  @media screen and (min-width: 64em) {
    div#amplitude-player {
      max-height: 715px; } }
  div#amplitude-left {
    padding: 0px;
    border-right: 1px solid #CFD8DC;
    width: 50%;
    display: flex;
    flex-direction: column; }
    div#amplitude-left img.album-art {
      width: 100%; }
    div#amplitude-left div#player-left-bottom {
      flex: 1;
      background-color: #F1F1F1;
      padding: 20px 10px; }
      div#amplitude-left div#player-left-bottom div#volume-container:after {
        content: "";
        display: table;
        clear: both; }

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    div#amplitude-player div#amplitude-left {
      width: 100%; }
      div#amplitude-player div#amplitude-left img[amplitude-song-info="cover_art_url"] {
        width: auto;
        height: auto; } }
  div#amplitude-right {
    padding: 0px;
    overflow-y: scroll;
    width: 50%;
    display: flex;
    flex-direction: column; }
    div#amplitude-right div.song {
      cursor: pointer;
      padding: 10px; }
      div#amplitude-right div.song div.song-now-playing-icon-container {
        float: left;
        width: 20px;
        height: 20px;
        margin-right: 10px; }
        div#amplitude-right div.song div.song-now-playing-icon-container img.now-playing {
          display: none;
          margin-top: 15px; }
      div#amplitude-right div.song div.play-button-container {
        display: none;
        background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/list-play-light.png") no-repeat;
        width: 22px;
        height: 22px;
        margin-top: 10px; }
      div#amplitude-right div.song div.play-button-container:hover {
        background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/list-play-hover.png") no-repeat; }
      div#amplitude-right div.song.amplitude-active-song-container div.song-now-playing-icon-container img.now-playing {
        display: block; }
      div#amplitude-right div.song.amplitude-active-song-container:hover div.play-button-container {
        display: none; }
      div#amplitude-right div.song div.song-meta-data {
        float: left;
        width: calc( 100% - 110px ); }
        div#amplitude-right div.song div.song-meta-data span.song-title {
          color: #272726;
          font-size: 16px;
          display: block;
          font-weight: 300;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis; }
        div#amplitude-right div.song div.song-meta-data span.song-artist {
          color: #607D8B;
          font-size: 14px;
          font-weight: bold;
          text-transform: uppercase;
          display: block;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis; }
      div#amplitude-right div.song img.bandcamp-grey {
        float: left;
        display: block;
        margin-top: 10px; }
      div#amplitude-right div.song img.bandcamp-white {
        float: left;
        display: none;
        margin-top: 10px; }
      div#amplitude-right div.song span.song-duration {
        float: left;
        width: 55px;
        text-align: center;
        line-height: 45px;
        color: #607D8B;
        font-size: 16px;
        font-weight: 500; }
    div#amplitude-right div.song:after {
      content: "";
      display: table;
      clear: both; }

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    div#amplitude-player div#amplitude-right {
      width: 100%; } }
  div#progress-container {
    width: 70%;
    float: left;
    position: relative;
    height: 20px;
    cursor: pointer;
    /*
      IE 11
    */ }
    div#progress-container:hover input[type=range].amplitude-song-slider::-webkit-slider-thumb {
      display: block; }
    div#progress-container:hover input[type=range].amplitude-song-slider::-moz-range-thumb {
      visibility: visible; }
    div#progress-container progress#song-played-progress {
      width: 100%;
      position: absolute;
      left: 0;
      top: 8px;
      right: 0;
      width: 100%;
      z-index: 60;
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
      height: 4px;
      border-radius: 5px;
      background: transparent;
      border: none;
      /* Needed for Firefox */ }
    @media all and (-ms-high-contrast: none) {
      div#progress-container *::-ms-backdrop, div#progress-container progress#song-played-progress {
        color: #00A0FF;
        border: none;
        background-color: #CFD8DC; } }
    @supports (-ms-ime-align: auto) {
      div#progress-container progress#song-played-progress {
        color: #00A0FF;
        border: none; } }
    div#progress-container progress#song-played-progress[value]::-webkit-progress-bar {
      background: none;
      border-radius: 5px; }
    div#progress-container progress#song-played-progress[value]::-webkit-progress-value {
      background-color: #00A0FF;
      border-radius: 5px; }
    div#progress-container progress#song-played-progress::-moz-progress-bar {
      background: none;
      border-radius: 5px;
      background-color: #00A0FF;
      height: 5px;
      margin-top: -2px; }
    div#progress-container progress#song-buffered-progress {
      position: absolute;
      left: 0;
      top: 8px;
      right: 0;
      width: 100%;
      z-index: 10;
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
      height: 4px;
      border-radius: 5px;
      background: transparent;
      border: none;
      background-color: #D7DEE3; }
    div#progress-container progress#song-buffered-progress[value]::-webkit-progress-bar {
      background-color: #CFD8DC;
      border-radius: 5px; }
    div#progress-container progress#song-buffered-progress[value]::-webkit-progress-value {
      background-color: #78909C;
      border-radius: 5px;
      transition: width .1s ease; }
    div#progress-container progress#song-buffered-progress::-moz-progress-bar {
      background: none;
      border-radius: 5px;
      background-color: #78909C;
      height: 5px;
      margin-top: -2px; }
    div#progress-container progress::-ms-fill {
      border: none; }
  @-moz-document url-prefix() {
    div#progress-container progress#song-buffered-progress {
      top: 9px;
      border: none; } }
    @media all and (-ms-high-contrast: none) {
      div#progress-container *::-ms-backdrop, div#progress-container progress#song-buffered-progress {
        color: #78909C;
        border: none; } }
    @supports (-ms-ime-align: auto) {
      div#progress-container progress#song-buffered-progress {
        color: #78909C;
        border: none; } }
    div#progress-container input[type=range] {
      -webkit-appearance: none;
      width: 100%;
      margin: 7.5px 0;
      position: absolute;
      z-index: 9999;
      top: -7px;
      height: 20px;
      cursor: pointer;
      background-color: inherit; }
    div#progress-container input[type=range]:focus {
      outline: none; }
    div#progress-container input[type=range]::-webkit-slider-runnable-track {
      width: 100%;
      height: 0px;
      cursor: pointer;
      box-shadow: 0px 0px 0px rgba(0, 0, 0, 0), 0px 0px 0px rgba(13, 13, 13, 0);
      background: #0075a9;
      border-radius: 0px;
      border: 0px solid #010101; }
    div#progress-container input[type=range]::-webkit-slider-thumb {
      box-shadow: 0px 0px 0px #000000, 0px 0px 0px #0d0d0d;
      border: 1px solid #00a0ff;
      height: 15px;
      width: 15px;
      border-radius: 16px;
      background: #00a0ff;
      cursor: pointer;
      -webkit-appearance: none;
      margin-top: -7.5px; }
    div#progress-container input[type=range]:focus::-webkit-slider-runnable-track {
      background: #00adfb; }
    div#progress-container input[type=range]::-moz-range-track {
      width: 100%;
      height: 0px;
      cursor: pointer;
      box-shadow: 0px 0px 0px rgba(0, 0, 0, 0), 0px 0px 0px rgba(13, 13, 13, 0);
      background: #0075a9;
      border-radius: 0px;
      border: 0px solid #010101; }
    div#progress-container input[type=range]::-moz-range-thumb {
      box-shadow: 0px 0px 0px #000000, 0px 0px 0px #0d0d0d;
      border: 1px solid #00a0ff;
      height: 15px;
      width: 15px;
      border-radius: 16px;
      background: #00a0ff;
      cursor: pointer; }
    div#progress-container input[type=range]::-ms-track {
      width: 100%;
      height: 0px;
      cursor: pointer;
      background: transparent;
      border-color: transparent;
      color: transparent; }
    div#progress-container input[type=range]::-ms-fill-lower {
      background: #003d57;
      border: 0px solid #010101;
      border-radius: 0px;
      box-shadow: 0px 0px 0px rgba(0, 0, 0, 0), 0px 0px 0px rgba(13, 13, 13, 0); }
    div#progress-container input[type=range]::-ms-fill-upper {
      background: #0075a9;
      border: 0px solid #010101;
      border-radius: 0px;
      box-shadow: 0px 0px 0px rgba(0, 0, 0, 0), 0px 0px 0px rgba(13, 13, 13, 0); }
    div#progress-container input[type=range]::-ms-thumb {
      box-shadow: 0px 0px 0px #000000, 0px 0px 0px #0d0d0d;
      border: 1px solid #00a0ff;
      height: 15px;
      width: 15px;
      border-radius: 16px;
      background: #00a0ff;
      cursor: pointer;
      height: 0px;
      display: block; }
    @media all and (-ms-high-contrast: none) {
      div#progress-container *::-ms-backdrop, div#progress-container input[type="range"].amplitude-song-slider {
        padding: 0px; }
      div#progress-container *::-ms-backdrop, div#progress-container input[type=range].amplitude-song-slider::-ms-thumb {
        height: 15px;
        width: 15px;
        border-radius: 10px;
        cursor: pointer;
        margin-top: -8px; }
      div#progress-container *::-ms-backdrop, div#progress-container input[type=range].amplitude-song-slider::-ms-track {
        border-width: 15px 0;
        border-color: transparent; }
      div#progress-container *::-ms-backdrop, div#progress-container input[type=range].amplitude-song-slider::-ms-fill-lower {
        background: #CFD8DC;
        border-radius: 10px; }
      div#progress-container *::-ms-backdrop, div#progress-container input[type=range].amplitude-song-slider::-ms-fill-upper {
        background: #CFD8DC;
        border-radius: 10px; } }
    @supports (-ms-ime-align: auto) {
      div#progress-container input[type=range].amplitude-song-slider::-ms-thumb {
        height: 15px;
        width: 15px;
        margin-top: 3px; } }
    div#progress-container input[type=range]:focus::-ms-fill-lower {
      background: #0075a9; }
    div#progress-container input[type=range]:focus::-ms-fill-upper {
      background: #00adfb; }

  div#control-container {
    margin-top: 25px;
    margin-top: 20px; }
    div#control-container div#repeat-container {
      width: 25%;
      float: left;
      padding-top: 20px; }
      div#control-container div#repeat-container div#repeat {
        width: 24px;
        height: 19px;
        cursor: pointer; }
        div#control-container div#repeat-container div#repeat.amplitude-repeat-off {
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/repeat-off.svg"); }
        div#control-container div#repeat-container div#repeat.amplitude-repeat-on {
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/repeat-on.svg"); }
      div#control-container div#repeat-container div#shuffle {
        width: 23px;
        height: 19px;
        cursor: pointer;
        float: right; }
        div#control-container div#repeat-container div#shuffle.amplitude-shuffle-off {
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/shuffle-off.svg"); }
        div#control-container div#repeat-container div#shuffle.amplitude-shuffle-on {
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/shuffle-on.svg"); }
    @media all and (-ms-high-contrast: none) {
      div#control-container *::-ms-backdrop, div#control-container div#control-container {
        margin-top: 40px;
        float: none; } }
    div#control-container div#central-control-container {
      width: 50%;
      float: left; }
      div#control-container div#central-control-container div#central-controls {
        width: 130px;
        margin: auto; }
        div#control-container div#central-control-container div#central-controls div#previous {
          display: inline-block;
          width: 40px;
          height: 40px;
          cursor: pointer;
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/prev.svg");
          background-repeat: no-repeat;
          float: left;
          margin-top: 10px;
          margin-right: -5px; }
        div#control-container div#central-control-container div#central-controls div#play-pause {
          display: inline-block;
          width: 60px;
          height: 60px;
          cursor: pointer;
          float: left; }
          div#control-container div#central-control-container div#central-controls div#play-pause.amplitude-paused {
            background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/play.svg"); }
          div#control-container div#central-control-container div#central-controls div#play-pause.amplitude-playing {
            background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/pause.svg"); }
        div#control-container div#central-control-container div#central-controls div#next {
          display: inline-block;
          width: 40px;
          height: 40px;
          cursor: pointer;
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/next.svg");
          background-repeat: no-repeat;
          float: left;
          margin-top: 10px;
          margin-left: -5px; }
    div#control-container div#volume-container {
      width: 25%;
      float: left;
      padding-top: 20px; }
      div#control-container div#volume-container div#shuffle-right {
        width: 23px;
        height: 19px;
        cursor: pointer;
        margin: auto; }
        div#control-container div#volume-container div#shuffle-right.amplitude-shuffle-off {
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/shuffle-off.svg"); }
        div#control-container div#volume-container div#shuffle-right.amplitude-shuffle-on {
          background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/shuffle-on.svg"); }
    div#control-container div.amplitude-mute {
      cursor: pointer;
      width: 25px;
      height: 19px;
      float: left; }
      div#control-container div.amplitude-mute.amplitude-not-muted {
        background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-players/volume.svg");
        background-repeat: no-repeat; }
      div#control-container div.amplitude-mute.amplitude-muted {
        background: url("https://521dimensions.com/img/open-source/amplitudejs/blue-player/mute.svg");
        background-repeat: no-repeat; }

  div#control-container:after {
    content: "";
    display: table;
    clear: both; }

  /* Small only */
  @media screen and (max-width: 39.9375em) {
    div#amplitude-player div#repeat-container div#repeat {
      margin-left: auto;
      margin-right: auto;
      float: none; }
    div#amplitude-player div#repeat-container div#shuffle {
      display: none; }
    div#amplitude-player div#volume-container div.volume-controls {
      display: none; }
    div#amplitude-player div#volume-container div#shuffle-right {
      display: block; } }
  /* Medium only */
  @media screen and (min-width: 40em) and (max-width: 63.9375em) {
    div#amplitude-player div#repeat-container div#repeat {
      margin-left: auto;
      margin-right: auto;
      float: none; }
    div#amplitude-player div#repeat-container div#shuffle {
      display: none; }
    div#amplitude-player div#volume-container div.volume-controls {
      display: none; }
    div#amplitude-player div#volume-container div#shuffle-right {
      display: block; } }
  /* Large and up */
  @media screen and (min-width: 64em) {
    div#amplitude-player div#repeat-container div#repeat {
      margin-left: 10px;
      margin-right: 20px;
      float: left; }
    div#amplitude-player div#volume-container div#shuffle-right {
      display: none; } }
  input[type=range].amplitude-volume-slider {
    -webkit-appearance: none;
    width: calc( 100% - 33px);
    float: left;
    margin-top: 10px;
    margin-left: 5px; }

  @-moz-document url-prefix() {
    input[type=range].amplitude-volume-slider {
      margin-top: 0px; } }
  @supports (-ms-ime-align: auto) {
    input[type=range].amplitude-volume-slider {
      margin-top: 3px;
      height: 12px;
      background-color: rgba(255, 255, 255, 0) !important;
      z-index: 999;
      position: relative; }

    div.ms-range-fix {
      height: 1px;
      background-color: #A9A9A9;
      width: 67%;
      float: right;
      margin-top: -6px;
      z-index: 9;
      position: relative; } }
  @media all and (-ms-high-contrast: none) {
    *::-ms-backdrop, input[type=range].amplitude-volume-slider {
      margin-top: -24px;
      background-color: rgba(255, 255, 255, 0) !important; } }
  input[type=range].amplitude-volume-slider:focus {
    outline: none; }

  input[type=range].amplitude-volume-slider::-webkit-slider-runnable-track {
    width: 75%;
    height: 1px;
    cursor: pointer;
    animate: 0.2s;
    background: #CFD8DC; }

  input[type=range].amplitude-volume-slider::-webkit-slider-thumb {
    height: 10px;
    width: 10px;
    border-radius: 10px;
    background: #00A0FF;
    cursor: pointer;
    margin-top: -4px;
    -webkit-appearance: none; }

  input[type=range].amplitude-volume-slider:focus::-webkit-slider-runnable-track {
    background: #CFD8DC; }

  input[type=range].amplitude-volume-slider::-moz-range-track {
    width: 100%;
    height: 1px;
    cursor: pointer;
    animate: 0.2s;
    background: #CFD8DC; }

  input[type=range].amplitude-volume-slider::-moz-range-thumb {
    height: 10px;
    width: 10px;
    border-radius: 10px;
    background: #00A0FF;
    cursor: pointer;
    margin-top: -4px; }

  input[type=range].amplitude-volume-slider::-ms-track {
    width: 100%;
    height: 1px;
    cursor: pointer;
    animate: 0.2s;
    background: transparent;
    /*leave room for the larger thumb to overflow with a transparent border */
    border-color: transparent;
    border-width: 15px 0;
    /*remove default tick marks*/
    color: transparent; }

  input[type=range].amplitude-volume-slider::-ms-fill-lower {
    background: #CFD8DC;
    border-radius: 10px; }

  input[type=range].amplitude-volume-slider::-ms-fill-upper {
    background: #CFD8DC;
    border-radius: 10px; }

  input[type=range].amplitude-volume-slider::-ms-thumb {
    height: 10px;
    width: 10px;
    border-radius: 10px;
    background: #00A0FF;
    cursor: pointer;
    margin-top: 2px; }

  input[type=range].amplitude-volume-slider:focus::-ms-fill-lower {
    background: #CFD8DC; }

  input[type=range].amplitude-volume-slider:focus::-ms-fill-upper {
    background: #CFD8DC; }

  input[type=range].amplitude-volume-slider::-ms-tooltip {
    display: none; }

  div#time-container span.current-time {
    color: #607D8B;
    font-size: 14px;
    font-weight: 700;
    float: left;
    width: 15%;
    text-align: center; }
  div#time-container span.duration {
    color: #607D8B;
    font-size: 14px;
    font-weight: 700;
    float: left;
    width: 15%;
    text-align: center; }

  div#time-container:after {
    content: "";
    display: table;
    clear: both; }

  div#meta-container {
    text-align: center;
    margin-top: 5px; }
    div#meta-container span.song-name {
      display: block;
      color: #272726;
      font-size: 20px;
      font-family: 'Open Sans', sans-serif;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis; }
    div#meta-container div.song-artist-album {
      color: #607D8B;
      font-size: 14px;
      font-weight: 700;
      text-transform: uppercase;
      font-family: 'Open Sans', sans-serif;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis; }
      div#meta-container div.song-artist-album span {
        display: block; }

  /*
    3. Layout
  */
  body .old {
    background-image: -webkit-linear-gradient(316deg, #3BD2AE 0%, #36BAC2 100%);
    background-image: linear-gradient(-226deg, #3BD2AE 0%, #36BAC2 100%);
    height: 100vh;
    -webkit-font-smoothing: antialiased;
    font-family: "Helvetica Neue",Helvetica,Roboto,Arial,sans-serif;
    line-height: 1.5; }
  div.amplitude-wave-form{
      margin-top: -14px;
  }
        
  div.amplitude-wave-form svg{
        stroke: #00a0ff;
        height: 50px;
        width: 100%;
        stroke-width: .5px;
  }
  div.amplitude-wave-form svg g{
    stroke: #00a0ff;
    height: 50px;
    width: 100%;
  }
  div.amplitude-wave-form svg g path{
    stroke: #00a0ff;
    height: 50px;
    width: 100%;
  }

  div#large-visualization{
      width: 100%;
      background-color: black;
      visibility: hidden;
    }
</style>
  <div id="blue-playlist-container">
			<div id="amplitude-player">
				<div id="amplitude-left">
					<img data-amplitude-song-info="cover_art_url" class="album-art"/>
          <div class="amplitude-visualization" id="large-visualization">
            </div>
					<div id="player-left-bottom">
						<div id="time-container">
							<span class="current-time">
								<span class="amplitude-current-minutes" ></span>:<span class="amplitude-current-seconds"></span>
							</span>
							<div id="progress-container">
								<div class="amplitude-wave-form">
                        </div>
                <input type="range" class="amplitude-song-slider"/>
								<progress id="song-played-progress" class="amplitude-song-played-progress"></progress>
								<progress id="song-buffered-progress" class="amplitude-buffered-progress" value="0"></progress>
							</div>
							<span class="duration">
								<span class="amplitude-duration-minutes"></span>:<span class="amplitude-duration-seconds"></span>
							</span>
						</div>
						<div id="control-container">
							<div id="repeat-container">
								<div class="amplitude-repeat" id="repeat"></div>
								<div class="amplitude-shuffle amplitude-shuffle-off" id="shuffle"></div>
							</div>
							<div id="central-control-container">
								<div id="central-controls">
									<div class="amplitude-prev" id="previous"></div>
									<div class="amplitude-play-pause" id="play-pause"></div>
									<div class="amplitude-next" id="next"></div>
								</div>
							</div>
							<div id="volume-container">
								<div class="volume-controls">
									<div class="amplitude-mute amplitude-not-muted"></div>
									<input type="range" class="amplitude-volume-slider"/>
									<div class="ms-range-fix"></div>
								</div>
								<div class="amplitude-shuffle amplitude-shuffle-off" id="shuffle-right"></div>
							</div>
						</div>
						<div id="meta-container">
							<span data-amplitude-song-info="name" class="song-name"></span>
							<div class="song-artist-album">
								<span data-amplitude-song-info="artist"></span>
								<span data-amplitude-song-info="album"></span>
							</div>
						</div>
					</div>
				</div>
				<div id="amplitude-right">
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="0">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Heavy Rain</span>
							<span class="song-artist">lebaston100</span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:14</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="1">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Airplane Flyover</span>
							<span class="song-artist">Suz_Soundcreations</span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">3:16</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="2">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Airplane Inside</span>
							<span class="song-artist">InspectorJ</span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">3:32</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="3">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Baby Crying</span>
							<span class="song-artist">Stevious42</span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">3:30</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="4">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Birds</span>
							<span class="song-artist"></span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:12</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="5">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Blender</span>
							<span class="song-artist"></span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:29</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="6">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Car Alarm</span>
							<span class="song-artist"></span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:29</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="7">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Cathedral Bells</span>
							<span class="song-artist"></span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">2:39</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="8">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Cats</span>
							<span class="song-artist"></span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">1:00</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="9">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Dusk To Dawn</span>
							<span class="song-artist">Emancipator</span>
						</div>
						<a href="https://emancipator.bandcamp.com/track/dusk-to-dawn-2" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:25</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="10">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Anthem</span>
							<span class="song-artist">Emancipator</span>
						</div>
						<a href="https://emancipator.bandcamp.com/track/anthem" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:40</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="10">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Anthem</span>
							<span class="song-artist">Emancipator</span>
						</div>
						<a href="https://emancipator.bandcamp.com/track/anthem" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:40</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="10">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Anthem</span>
							<span class="song-artist">Emancipator</span>
						</div>
						<a href="https://emancipator.bandcamp.com/track/anthem" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:40</span>
					</div>
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="10">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">Anthem</span>
							<span class="song-artist">Emancipator</span>
						</div>
						<a href="https://emancipator.bandcamp.com/track/anthem" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:40</span>
					</div>
          {% for song in site.data.songs %}
					<div class="song amplitude-song-container amplitude-play-pause" data-amplitude-song-index="{{ forloop.index0 }}">
						<div class="song-now-playing-icon-container">
							<div class="play-button-container">
							</div>
							<img class="now-playing" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/now-playing.svg"/>
						</div>
						<div class="song-meta-data">
							<span class="song-title">{{ song.name }}</span>
							<span class="song-artist">{{ song.artist }}</span>
						</div>
						<a href="https://avishaan.com/dog-socialization" class="bandcamp-link" target="_blank">
							<img class="bandcamp-grey" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-grey.svg"/>
							<img class="bandcamp-white" src="https://521dimensions.com/img/open-source/amplitudejs/blue-player/bandcamp-white.svg"/>
						</a>
						<span class="song-duration">5:40</span>
					</div>
          {% endfor %}
				</div>
			</div>
		</div>

  <div id="rootie">
  </div>
  <h1>Test</h1>
  <h1>{{ site.data.navigation.main[0].title }}</h1>
  <h1>{{ site.data.songs[0].name}}</h1>

<script>
  let bandcampLinks = document.getElementsByClassName('bandcamp-link');

  for( var i = 0; i < bandcampLinks.length; i++ ){
    bandcampLinks[i].addEventListener('click', function(e){
      e.stopPropagation();
    });
  }


  let songElements = document.getElementsByClassName('song');

  for( var i = 0; i < songElements.length; i++ ){
    /*
      Ensure that on mouseover, CSS styles don't get messed up for active songs.
    */
    songElements[i].addEventListener('mouseover', function(){
      this.style.backgroundColor = '#00A0FF';

      this.querySelectorAll('.song-meta-data .song-title')[0].style.color = '#FFFFFF';
      this.querySelectorAll('.song-meta-data .song-artist')[0].style.color = '#FFFFFF';

      if( !this.classList.contains('amplitude-active-song-container') ){
        this.querySelectorAll('.play-button-container')[0].style.display = 'block';
      }

      this.querySelectorAll('img.bandcamp-grey')[0].style.display = 'none';
      this.querySelectorAll('img.bandcamp-white')[0].style.display = 'block';
      this.querySelectorAll('.song-duration')[0].style.color = '#FFFFFF';
    });

    /*
      Ensure that on mouseout, CSS styles don't get messed up for active songs.
    */
    songElements[i].addEventListener('mouseout', function(){
      this.style.backgroundColor = '#FFFFFF';
      this.querySelectorAll('.song-meta-data .song-title')[0].style.color = '#272726';
      this.querySelectorAll('.song-meta-data .song-artist')[0].style.color = '#607D8B';
      this.querySelectorAll('.play-button-container')[0].style.display = 'none';
      this.querySelectorAll('img.bandcamp-grey')[0].style.display = 'block';
      this.querySelectorAll('img.bandcamp-white')[0].style.display = 'none';
      this.querySelectorAll('.song-duration')[0].style.color = '#607D8B';
    });

    /*
      Show and hide the play button container on the song when the song is clicked.
    */
    songElements[i].addEventListener('click', function(){
      this.querySelectorAll('.play-button-container')[0].style.display = 'none';
    });
  }

  /*
    Initializes AmplitudeJS
  */
  var songs = [
      {
        "name": "Heavy Rain",
        "artist": "lebaston100",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/heavy rain.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Airplane Flyover",
        "artist": "Suz_Soundcreations",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/airplane flyover.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Airplane Inside",
        "artist": "InspectorJ",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/airplane inside.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Baby Crying",
        "artist": "Stevious42",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/baby cry.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Birds",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/birds.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Blender",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/blender.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Car Alarm",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/car alarm.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Cathedral Bells",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/cathedral bells.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Cats",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/cats.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Children Playing",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/children playing.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Clock Bell",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/clock bell.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Crowd Cheering",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/crowd cheering.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Dog Barking",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/crowd cheering.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Door Knocking",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/door knock.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Electric Razor",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/electric razor.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Espresso Coffee Machine",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/espresso coffee machine.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Female Voices Cafe",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/female voices cafe.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Fire Engine",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/fire engine.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Fireworks",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/fireworks.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Garbage Truck",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/garbage truck.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Hair Dryer",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/hair dryer.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Heavy Rain",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/heavy rain.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "iPhone Typing",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/iphone typing.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Jackhammer",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/jackhammer.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Lawn Mower",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/lawn mower.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Leaf Blower",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/leaf blower.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Manhattan Ambulance",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/manhatten ambulance.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Microwave",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/microwave.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Motorcycles",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/motorcycles.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Police",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/police.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Popcorn",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/popcorn.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Pots Clanking",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/pots clanking.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Radio Static",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/radio static.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Small Dog Growling",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/small dog growling rope.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Smoke Detector",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/smoke detector.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Thunder",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/thunder.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Traffic with Horns",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/traffic with horns.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Vacuum",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/vacuum.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      },
      {
        "name": "Waves",
        "artist": "",
        "album": "Puppy Socialization",
        "url": "/assets/dog-socialization/waves.mp3",
        "cover_art_url": "/assets/dog-socialization/album.jpg"
      }
    ];
  Amplitude.init({
    "songs": {{ site.data.songs | jsonify }},
    "callbacks": {
          'play': function(){
              document.getElementById('album-art').style.visibility = 'hidden';
              document.getElementById('large-visualization').style.visibility = 'visible';
          },

          'pause': function(){
              document.getElementById('album-art').style.visibility = 'visible';
              document.getElementById('large-visualization').style.visibility = 'hidden';
          }
      },
    waveforms: {
      sample_rate: 50
    }
  });
  document.getElementById('large-visualization').style.height = document.getElementById('album-art').offsetWidth + 'px';

</script>
<script type="text/javascript" src="/assets/js/test.js"></script>
<script>
console.log('test');
console.log('{{ site.data.navigation.main[0].title }}')
</script>

{% comment %}


{% endcomment %}