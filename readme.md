![header](https://capsule-render.vercel.app/api?type=Waving&color=4e63d6&height=200&section=header&text=Hello_World!&fontSize=50&animation=fadeIn&fontColor=DDDDDD)
# 안녕하세요

>ㄹㅇㅋㅋ

>ㄹㅇㅋㅋ

## 만든파일

My ProjectFile
-------------------------
```c
int main(){
    printf("Hello world");
    return 0;
}
```
**시로코**

![Alt text](https://w.namu.la/s/dd43b2a227882cb474cdc019739972869f4a69188a21abe0d0fde5471949dffed65c4a0cf172820ea03b8fad96ad7f4673647d836a472d1e2408ab50cc6a6431befb282a72b3cb082b759828ad7d846a36c642cfe5a088e6b2e6e656d92c79eb)
>내최애캐

**호시노**
![Alt text](https://blue-utils.me/img/common/chara/intro/jp/hoshino_swimsuit.jpg)


**아야네**
![Alt text](https://w.namu.la/s/f7dc078082b7c0247a7aef40af7bf01cfdf145c6dd42a0ce35bb06b0bc0f7accf79500386e7b40c4e5521da471a805676d6bfedc6a2fcb0d3f9f20561f293d2d79b1cf3854c2c59b98578570724e66cd1f63de161c8853b9f78eb8f2672435874e662462bac7c5830a7c91c81fe18317)


## 만들고 있는 게임
-----------------------------------
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.SceneManagement;
using System;
using TMPro;

public class GameManager : MonoBehaviour
{
    public bool[] isEntrance;

    // 죽었을 때 리스폰
    public bool isDie;

    // 엔딩
    public bool isEnd;

    public float endingPoint;

    public List<Vector3> roomPoint;

    public int roomCount;
    float randomEntranceValue;

    public TextMeshProUGUI randomEntranceText;

    public Transform playerPos;

    // 중소형 개체
    public GameObject[] Objects;

    // ObjectPool
    public GameObject[] rooms;
    public GameObject[] roomPool_0;
    public GameObject[] roomPool_1;
    public GameObject[] roomPool_2;
    public GameObject[] roomPool_3;

    public int RoomCount
    {
        get
        {
            return roomCount;
        }
        set
        {
            roomCount = value;
            print(roomCount);
        }
    }

    public float RandomEntranceValue
    {
        get
        {
            return randomEntranceValue;
        }
        set
        {
            randomEntranceValue = value;
            randomEntranceValue = Mathf.Clamp(randomEntranceValue, 0, 100);
            randomEntranceText.text = randomEntranceValue.ToString("F2") + "%";
        }
    }

    private void Awake()
    {
        for (int j = 0; j < roomPool_0.Length; j++)
        {
            GameObject obj = Instantiate(rooms[0], Vector3.zero, Quaternion.identity);
            obj.SetActive(false);
            roomPool_0[j] = obj;
        }
        for (int j = 0; j < roomPool_1.Length; j++)
        {
            GameObject obj = Instantiate(rooms[1], Vector3.zero, Quaternion.identity);
            obj.SetActive(false);
            roomPool_1[j] = obj;
        }
        for (int j = 0; j < roomPool_2.Length; j++)
        {
            GameObject obj = Instantiate(rooms[2], Vector3.zero, Quaternion.identity);
            obj.SetActive(false);
            roomPool_2[j] = obj;
        }
        for (int j = 0; j < roomPool_3.Length; j++)
        {
            GameObject obj = Instantiate(rooms[3], Vector3.zero, Quaternion.identity);
            obj.SetActive(false);
            roomPool_3[j] = obj;
        }
    }

    public void Entrance()
    {
        if (!isEntrance[0] && !isEntrance[1] && !isEntrance[2] && !isEntrance[3] && !isEntrance[4] && !isEntrance[5])
        {
            isEntrance[0] = true;
        }
        else if (!isEntrance[1] && !isEntrance[2] && !isEntrance[3] && !isEntrance[4] && !isEntrance[5])
        {
            isEntrance[1] = true;
        }
        else if (!isEntrance[2] && !isEntrance[3] && !isEntrance[4] && !isEntrance[5])
        {
            isEntrance[2] = true;
        }
        else if (!isEntrance[3] && !isEntrance[4] && !isEntrance[5])
        {
            isEntrance[3] = true;
        }
        else if (!isEntrance[4] && !isEntrance[5])
        {
            isEntrance[4] = true;
        }
        else if (!isEntrance[5])
        {
            isEntrance[5] = true;
        }

        if (isEntrance[0] && isEntrance[1] && isEntrance[2] && isEntrance[3] && isEntrance[4] && isEntrance[5])
        {
            isEnd = UnityEngine.Random.Range(0f, 100f) > endingPoint;
            if (isEnd)
            {

            }
            else
            {
                endingPoint++;
            }
        }
    }

    public void MakeRoom(Vector3 vec)
    {
        if (!roomPoint.Contains(vec))
        {
            int ran = UnityEngine.Random.Range(0, 4);

            switch (ran)
            {

                case 0:
                    for (int i = 0; i < roomPool_0.Length; i++)
                    {
                        if (roomPool_0[i].activeSelf == false)
                        {
                            roomPool_0[i].transform.position = vec;
                            roomPool_0[i].SetActive(true);
                            break;
                        }
                    }
                    break;
                case 1:
                    for (int i = 0; i < roomPool_1.Length; i++)
                    {
                        if (roomPool_1[i].activeSelf == false)
                        {
                            roomPool_1[i].transform.position = vec;
                            roomPool_1[i].SetActive(true);
                            break;
                        }
                    }
                    break;
                case 2:
                    for (int i = 0; i < roomPool_2.Length; i++)
                    {
                        if (roomPool_2[i].activeSelf == false)
                        {
                            roomPool_2[i].transform.position = vec;
                            roomPool_2[i].SetActive(true);
                            break;
                        }
                    }
                    break;
                case 3:
                    for (int i = 0; i < roomPool_3.Length; i++)
                    {
                        if (roomPool_3[i].activeSelf == false)
                        {
                            roomPool_3[i].transform.position = vec;
                            roomPool_3[i].SetActive(true);
                            break;
                        }
                    }
                    break;
            }

            roomPoint.Add(vec);
        }
        
    }
}
```
--------------------------------------