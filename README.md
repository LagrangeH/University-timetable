## Проблема
Я учусь в университете, на сайте которого выкладывается расписание в формате xlsx. Мне не удобдно постоянно складировать схожие файлы и постоянно сверять изменилось ли оно.
## Решение
Я написал незамысловатые скрипты на bash и python, которые берут хэш-сумму старого расписания, удаляют его, скачивает новое и сравнивают хэш суммы. Если же расписания нет, то скрипт сам скачает его. Скрипт на python также определяет операционную систему, чтобы правильно подобрать директорию. Bash скрипт будет работать только на linux и MacOS, он не требует для устанвоки никаких модулей. Далее будет приведена инструкция по настройке на разных операционных системах. 
### Windows 
Для Windows никаких лишних настроек не требуется, просто скачайте python-файл, откройте терминал в директории со каченным файлом. Для этого в поисковой строке напишите 
```
cmd
```
![image](https://user-images.githubusercontent.com/77790965/176429849-1b4b0bdc-8218-4f39-8b8b-b48699ea3d76.png)

В Windows 11 терминал также можно открыть нажав ПКМ в директории и нажать кнопку "Открыть в терминале"
![image](https://user-images.githubusercontent.com/77790965/176430193-e52a849f-4a4e-45ae-9728-466a82349d6b.png)

Далее введите 
```python
python get-timetable.py
```
Скрипт скачает раписание и сообщит изменилось ли оно.
![image](https://user-images.githubusercontent.com/77790965/176430969-2ef38e47-f6a9-4a73-836f-394d2f279ae3.png)

### Linux 
Для работы срипта нужно установить некоторые пакеты вначале для системы
```bash
sudo apt install python-tk python3-pip
```
Потом необходимо установить python-модуль requests 
```
pip3 install requests
```
Теперь ровно как и в Windows нужно открыть терминал в папке со скриптом. Для этого в ubuntu нужно нажать ПКМ и нажать "Open in terminal".

![image](https://user-images.githubusercontent.com/77790965/176432071-fdbec518-77fe-4159-9d06-e5aaa8998923.png)

Обратите внимание, что скрипт нужно запускать с python версии 3
```python
python3 get-timetable.py
```
![image](https://user-images.githubusercontent.com/77790965/176432358-cc8e024e-c022-424f-90cc-2e03edc70e3c.png)

### MacOS

Для начала установите модуль requests 
```
pip3 install requests
```
Далее необходимо установить SSL сертификаты. Для этго нужно пройти в системную папку Программы -> Папка с установленным Python и запустить Install Certificates.command .
![Snimok_ekrana_2022-06-29_v_15_15_39](https://user-images.githubusercontent.com/77790965/176434299-815d14e4-dd34-4cd9-ac3c-ba140cb310ef.png)

После завершения процесса вы млжете закрыт ьвыпавшее окно терминала.
Запустите скрипт командой 
```python
python3 get-timetable.py
```
![Snimok_ekrana_2022-06-29_v_15_16_34](https://user-images.githubusercontent.com/77790965/176434495-ece4b633-eef7-4bb6-a802-55d87088c45f.png)

## Продвинутые настройки
В первую очередь скрипт нацелен на простоту в использовании, он скачивает расписание в системную директорию Загрузки или на рабочий стол(Windows). Но её можно изменить, для этого отредактируйте одну из следующих строк, в зависимости от используемой ОС.
![image](https://user-images.githubusercontent.com/77790965/176435206-f15cf18f-7679-4ec4-9cc6-0843c9ac2090.png)

Скрипт изначально нацелен на скачивание конкретного файла, но его легко можно изменить, для этого нужно отредактировать перменную url на строке 9. Необходимо указакать ссылку именно на скачивание файла, а не на страницу, где он расположен.
![image](https://user-images.githubusercontent.com/77790965/176435522-e3e61197-d76f-434d-b5f9-9b254b82854c.png)

Для этого нажмите ПКМ по ссылке загрузки и нажмите "Копировать адрес ссылки".
![image](https://user-images.githubusercontent.com/77790965/176435993-4308d9a7-9003-4904-92de-a0ab99a23597.png)

### Bash скрипт
Для его использования просто сделайте файл исполяемым и запустите
```bash
chmod +x ./get-timetable.sh
./get-timetable.sh
```
