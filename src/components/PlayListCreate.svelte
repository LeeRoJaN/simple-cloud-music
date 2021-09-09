<script>
      import { currentSongStore } from '../store/play';

    import { addOrRemoveTrackFromPlaylist } from '../api/playlist';

    import Lazy from 'svelte-lazy';

    export let songList = JSON.parse(localStorage.getItem('mySongList'));

    import { Toast } from '../utils/common';

    export let customCoverUrl = null;

    //添加歌曲到歌单
    async function addMyList(song) {

    let id = song.id;//歌单id

    const res = await addOrRemoveTrackFromPlaylist({ op:'add', pid:id, tracks:$currentSongStore.id});
    if (res.code === 200) {
        Toast(`😂 添加成功~`, 2000);
      } else {
        Toast(`😂 添加失败啦~`, 2000);
      }
    }
  </script>

  <div>
    {#each songList as song, i}
        {#if song.userId === song.creator.userId}

        <div class="song" on:click={addMyList(song)}>

        <div class="song-cover">
          <Lazy height={46}>
            <img
              class="img-song"
              src={customCoverUrl ? customCoverUrl : song.coverImgUrl.replace(/^http:/, 'https:') + '?param=100y100'}
              alt=""
            />
          </Lazy>
        </div>
        <div class="song-info" style="max-width:{localStorage.getItem('fullWidth') - 72}px;">
          <div class="song-name">
            {song.name}
            <span class="alia">
              {song.alia && song.alia.length > 0 ? `(${song.alia[0]})` : ''}
            </span>
          </div>
          <!-- <div class="song-songer">
            {songerListToStr(song.ar)}
            <span>{song.al.name === '' ? '' : `- ${song.al.name}`}</span>
          </div> -->
        </div>
      </div>
      {/if}
      <!-- <Song {song} index={i} on:songClick={getSongClick} /> -->
    {/each}
  </div>



  <style>
    .song {
      font-size: 14px;
      text-align: center;
      align-items: center;
      padding: 14px;
      display: flex;
      height: 60px;
      justify-content: space-between;
      border-bottom: 1px solid rgba(197, 197, 197, 0.3);
      box-sizing: border-box;
    }
    .song-cover {
      width: 46px;
      height: 46px;
      margin-right: 6px;
      border-radius: 4px;
      overflow: hidden;
      background-color: #fff;
      box-sizing: border-box;
    }
    .img-song {
      width: 100%;
      object-fit: cover;
    }
    .song-info {
      padding-top: 4px;
      text-align: left;
      flex: auto;
    }
    .song-name {
      white-space: nowrap;
      text-overflow: ellipsis;
      overflow: hidden;
      font-size: 18px;
    }
    .song-songer {
      margin-top: 6px;
      margin-bottom: 6px;
      color: rgb(185, 185, 185);
      white-space: nowrap;
      text-overflow: ellipsis;
      overflow: hidden;
    }
  </style>
