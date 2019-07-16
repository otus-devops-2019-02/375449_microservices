	ДЗ к занятию №17 (docker-4)

### Сделано:

	1. Docker контейнеры post и comment были помещены в обе сети
	2. Установил docker-compose на локальную машину
	3. собрал образы приложения reddit с помощью docker-compose
	4. Запустил приложение reddit с помощью dockercompose 
	
	Базовое имя проекта образуется при помощи container_name

<details>
<summary>ДЗ к занятию №16 (docker-3)</summary>

### Сделано:

	1. Описал и собрал Docker-образы для сервисного приложения
	2. Оптимизировал работу с Docker-образами
	3. Запустил и работал с  приложения на основе Docker-образов, оценил
удобства запуска контейнеров при помощи docker run
</details>

<details>
<summary>ДЗ к занятию №15 (docker-2)</summary>

### Сделано:

	1. Создал docker host
	2. Создал своего образа
	3. Поработал с Docker Hub
</details>

<details>
<summary>ДЗ к занятию №14 (docker-1)</summary>

### Сделано:

	1. Установил Docker
	2. Запустил контейнер hello-world 
	3. Работа с образами Docker 
</details>

<details>
<summary>ДЗ к занятию №13 (ansible-4)</summary>

### Сделано:

	1. Выполнил локальную разработку при помощи Vagrant, доработка ролей для провижининга в Vagrant
	2. Произвёл тестирование ролей при помощи Molecule и Testinfra
	3. Сделал переключение сбора образов пакером на использование ролей
</details>


<details>
<summary>ДЗ к занятию №12 (ansible-3)</summary>

### Сделано:

	1. Перенес созданные плейбуки в раздельные роли
	2. Описал два окружения
	3. Использовал коммьюнити роль nginx
	4. Использовал Ansible Vault для наших окружений
</details>

<details>
<summary>ДЗ к занятию №11 (ansible-2)</summary>

### Сделано:

	1. Создал плейбук с одним сценарием для деплоя приложения
	2. Создал плейбук с несколькими сценариями для деплоя приложения
	3. Создал три плейбука для настройки сервера прилодений, базы данных и деплоя кода
	4. Изменил провижиниг в packer на ansible
</details>


<details>
<summary>ДЗ к занятию №10 (ansible-1)</summary>

### Сделано:

	1. Установил Ansible
	2. Познакомился с базовыми функциями и инвентори
	3. Опробовал различные модули на подготовленной в прошлых ДЗ инфраструктуре
	4. Написал простой плейбук
	
	Если в выводе команд ansible или ansible-playbook есть:
	changed=1
	
	то на сервере произошли изменения
</details>
	

<details>
<summary>ДЗ к занятию №9 (terraform-2)</summary>

### Сделано:

	1. Импортировал существующее правило файервола в файл состояния терраформ (terraform import)
	2. Проверил взаимосвязи ресурсов на примере создания ресурса IP-адреса
	3. Средствами packer создал два новых шаблона для app и db
	4. Создал модули для app, db и vpc
	5. Проверил работу параметризации модулей (на примере файервола)
	6. Создал две директории с конфигурационными файлами для stage и prod
	7. Создал хранилище с помощью модуля storage-bucket из реестра модулей
</details>

<details>
<summary>ДЗ к занятию №8 (terraform-1)</summary>

### Сделано:

	1. Определил input переменную для приватного ключа - private_key_path
	2. Определил input переменную для задания зоны - zone
	3. Отформатировал командой terraform fmt
	4. Сделал рядом файл terraform.tfvars.example
	
</details>
	
<details>
<summary>ДЗ к занятию №7 (packer-base)</summary>

### Сделано:
 
	1. Установил packer
	2. Подготовил образ reddit-base
	3. Создал ubuntu16.json
	4. Создал и добавил переменные в файл variables.json
	5. Скрыл в .gitignore файл variables.json

</details>
<details>
<summary>ДЗ к занятию №6 (cloud-testapp)</summary>

### Данные для подключения:
testapp_IP = 35.240.16.90
testapp_port = 9292
### Создание ВМ с автозапуском скрипта
gcloud compute instances create reddit-app --boot-disk-size=10GB \
--image-family ubuntu-1604-lts --image-project=ubuntu-os-cloud \
--machine-type=g1-small --tags puma-server --restart-on-failure \
--metadata-from-file startup-script=dchirkov_infra/startup_script.sh \
--zone europe-west1-b
### Создание правила файервола посредством команды gcloud
gcloud compute firewall-rules create default-puma-server --allow=tcp:9292 --target-tags puma-server
</details>

<details>

<summary>ДЗ к занятию №5 (cloud-bastion)</summary>

### SSH-подключение к someinternalhost в одну команду
Подключиться к VM someinternalhost 10.132.0.5 через VM bastion 130.211.109.49 :

ssh -J appuser@130.211.109.49 appuser@10.132.0.5

### SSH-подключение к someinternalhost через alias
Подключение через alias - создаём config-файл пользователя на локальной машине

$ cat .ssh/config
Host bastion
HostName 130.211.109.49
User appuser
Host someinternalhost
HostName 10.132.0.5
ProxyJump bastion
User appuser

### Подключение по VPN
Данные для подключения:

bastion_IP = 130.211.109.49
someinternalhost_IP = 10.132.0.5

</details>
