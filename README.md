#!/bin/bash

#проверка аргументов
if [ "$#" -ne 2 ]; then
echo "Please, enter directory and file extension"
exit 1
fi

#объявление переменных
DIRECTORY=$1
EXTENSION=$2

#проверка сущестовования директории
if [ ! -d "$DIRECTORY" ]; then
echo "Directory isn't found"
exit 1
fi

#поиск файлов
FILE=$(find "$DIRECTORY" -type f -name "*.$EXTENSION" | xargs -n 1 basename)

#выводим данные
if [ ! -z "$FILE" ]; then
echo "$FILE"
else
echo "Files with extension $EXTENSION isn't found"
fi
