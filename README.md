Ansible ffmpeg role
=========

This role sets out to compile ffmpeg and various packages from source so that your servers will either have the latest version of ffmpeg and it's packages or consistent versions across servers.

Role Variables
--------------

| Variable                       | Default                               | Comments                                                 |
| :---                           | :---                                  |:---                                                      |
| `ffmpeg_source_dir` | /opt/ffmpeg/src |  |
| `ffmpeg_build_dir` | /opt/ffmpeg/ffmpeg_build |  |
| `ffmpeg_bin_dir` | /opt/ffmpeg/bin |  |
| `ffmpeg_repo` | git://source.ffmpeg.org/ffmpeg.git |  |
| `ffmpeg_repo_dir` | ffmpeg |  |
| `ffmpeg_version` | HEAD |  |
| `ffmpeg_config_opt` |  |  |
| `ffmpeg_neon_enable` | false | Enable neon optimisation |
| `ffmpeg_yasm_repo` | git://github.com/yasm/yasm.git |  |
| `ffmpeg_yasm_repo_dir` | yasm |  |
| `ffmpeg_yasm_version` | HEAD |  |
| `ffmpeg_libfdkaac_enable` | true |  |
| `ffmpeg_libfdkaac_repo` | git://github.com/mstorsjo/fdk-aac.git |  |
| `ffmpeg_libfdkaac_repo_dir` | libfdkaac |  |
| `ffmpeg_libfdkaac_version` | HEAD |  |
| `ffmpeg_libvpx_enable` | true |  |
| `ffmpeg_libvpx_repo` | https://chromium.googlesource.com/webm/libvpx.git |  |
| `ffmpeg_libvpx_repo_dir` | libvpx |  |
| `ffmpeg_libvpx_version` | HEAD |  |
| `ffmpeg_opus_enable` | true |  |
| `ffmpeg_opus_repo` | https://github.com/xiph/opus.git |  |
| `ffmpeg_opus_repo_dir` | opus |  |
| `ffmpeg_opus_version` | HEAD |  |
| `ffmpeg_speex_enable` | true |  |
| `ffmpeg_speex_repo` | https://github.com/xiph/speex.git |  |
| `ffmpeg_speex_repo_dir` | speex |  |
| `ffmpeg_speex_version` | HEAD |  |
| `ffmpeg_x264_enable` | true |  |
| `ffmpeg_x264_repo` | git://git.videolan.org/x264.git |  |
| `ffmpeg_x264_repo_dir` | x264 |  |
| `ffmpeg_x264_version` | HEAD |  |
| `ffmpeg_x264_config_opt` |  |  |
| `ffmpeg_x265_enable` | true |  |
| `ffmpeg_x265_repo` | https://bitbucket.org/multicoreware/x265 |  |
| `ffmpeg_x265_repo_dir` | x265 |  |
| `ffmpeg_x265_version` | tip |  |
| `ffmpeg_h264_omx_enable` | false | Enable h264_omx hardware h264 encoder |
| `ffmpeg_h264_qsv_enable` | false | Not fully implemented |
| `ffmpeg_h264_nvenc_enable` | false | Not fully implemented |

Raspberry Pi
-------
Only the Raspberry Pi 2 and 3 currently work. Other models on the armv6 chipset fails when trying to run ffmpeg

Raspberry Pi model A, model B, model B+ and zero will require some variables to be set to avoid the "Illegal Instruction" error for libx264 and ffmpeg. However, only x264 has been made to work so far.

libx265 and libspeex currently do not compile for all models of Raspberry Pi in this role and therefore need to be disabled with

```
ffmpeg_speex_enable: false
ffmpeg_x265_enable: false
```

Limitations
-------
- This role will compile ffmpeg and various packages from source and will therefore take a long time to run on slower systems (Hours in some cases)
- There are issues with this role in compiling libx265 and libspeex for the Raspberry Pi
- Enabling Intel QSV and Nvidia's nvenc require additional files to work and is not fully implemented in this role. Please see [https://trac.ffmpeg.org/wiki/HWAccelIntro](https://trac.ffmpeg.org/wiki/HWAccelIntro) for more details.

License
-------

BSD
