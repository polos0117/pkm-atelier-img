# pkm-atelier-img

`pkm-atelier` 의 그림 저장소다. 코드는 [pkm-atelier](https://github.com/polos0117/pkm-atelier) 에 있다.

## 왜 나눠 두나

앞선 저장소(`atelier`)는 그림을 코드와 같이 두었다가 `.git` 이 323 MB 가 되었다.
그중 250 MB 가 그림이고, 이력을 지워도 46 MB 밖에 안 줄어든다 — 옮기려면 이력을
다시 써야 하고 그러면 남의 clone 이 전부 깨진다. 처음부터 나눠 두면 그 일이 없다.

GitHub 의 자리는 저장소마다 따로 셈한다(권장 1 GB, Pages 로 낸 사이트 1 GB).
여기가 그 한 몫을 따로 받는다.

## 자리

```
img/<파일>.webp        원본. 폼 초상은 1024×1536 (2:3)
img/thumb/<같은 이름>   목록용. 긴 변 512
```

파일 이름이 곧 등록 정보다. 차례는 뒤에서부터 벗긴다.

```
<카드>_<폼>_<화풍>_<성별>.webp          폼 초상    피카츄_light_cinematic_semi_real_f.webp
<카드>_<폼>_<화풍>_<성별>_actionN.webp  연출컷     폼마다 있어도 되고 없어도 된다
<카드>_<화풍>_<성별>_casualN.webp       일상컷     일상컷은 폼을 안 탄다
```

성별은 지금 `f` 만 쓰지만 이름에는 반드시 적는다. 나중에 `m` 을 더해도 옛 파일의
뜻이 안 바뀌게 하려는 것이다.

## 올린 뒤에 할 일

여기 파일이 있다고 화면에 뜨지는 않는다. `pkm-atelier` 에서 등록을 거쳐야 한다.

```bash
python3 tools/register-images.py     # data/img.json 에 적는다
python3 tools/make-thumbs.py         # img/thumb/ 를 만든다
```

썸네일은 없어도 화면이 원본으로 되돌아가 뜨기는 한다. 다만 목록이 원본을 그대로
받아 무거워진다.

Pages 를 켜 두어야 `https://polos0117.github.io/pkm-atelier-img/img/…` 로 읽힌다.
`.nojekyll` 은 Pages 가 파일을 있는 그대로 내보내게 한다.

화풍 key는 코드 저장소의 `lib/prompt-spec.js` (`ART_STYLES`)를 따른다.
도감과 등록 도구가 읽는 `data/style.json`도 그 목록에서 생성한다.
