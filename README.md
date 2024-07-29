# Домашнее задание к занятию «Хранение в K8s. Часть 2» - Сергей Ситкарёв

## Задание 1

Создать Deployment приложения, использующего локальный PV, созданный вручную.

Создать Deployment приложения, состоящего из контейнеров busybox и multitool.

[deployment](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/src/deployment.yaml)

Создать PV и PVC для подключения папки на локальной ноде, которая будет использована в поде.

[pv](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/src/pv.yaml)

[pvc](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/src/pvc.yaml)

Продемонстрировать, что multitool может читать файл, в который busybox пишет каждые пять секунд в общей директории.

![Задание1](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/1.jpg)

Удалить Deployment и PVC. Продемонстрировать, что после этого произошло с PV. Пояснить, почему.

persistentvolume-controller может удалить данные только по пути /tmp/.+, а требуется удалить из /data/pvc

![Задание1](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/2.jpg)

Продемонстрировать, что файл сохранился на локальном диске ноды. 

![Задание1](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/3.jpg)

Удалить PV. Продемонстрировать что произошло с файлом после удаления PV. Пояснить, почему.

После удаления PV, файл сохранился на диске ноды, чтобы удалился нужно установить политику persistentVolumeReclaimPolicy: Recycle

## Задание 2

Создать Deployment приложения, которое может хранить файлы на NFS с динамическим созданием PV.

Включить и настроить NFS-сервер на MicroK8S.

![Задание2](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/4.jpg)

Создать Deployment приложения состоящего из multitool

[deployment-nfs](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/src/deployment-nfs.yaml)

и подключить к нему PV, созданный автоматически на сервере NFS.

[pvc-nfs](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/src/pvc-nfs.yaml)

Продемонстрировать возможность чтения и записи файла изнутри пода.

![Задание2](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/5.jpg)

![Задание2](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/6.jpg)

![Задание2](https://github.com/SSitkarev/2.2-k8s-storage_2/blob/main/img/7.jpg)