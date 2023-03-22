# Infrastructure repostiory

Wstępne informacje dot. infrastruktury:

- IaC w oparciu o narzędzie Ansible
- Infrastruktura oparta o zbiór kontenerów
- Kontenery będą zarządzane za pomocą docker compose

## Ansible

Rolą ansible w projekcie będzie inicjalizacja serwera o przygotowane playbook'i:
- ```initialize_server.yml```
- ```install_docker.yml```
- ```configure_project.yml```

### initialize_server.yml
będzie odpowiedzialny za wstępną konfiguracje serwera:
- instalacja i konfiguracja nginx (load balancer dla kontenerów)
- ...


### install_docker.yml
będzie odpowiedzialny za instalacje dockera na serwerze:

### configure_project.yml
będzie odpowiedzialny za konfiguracje projektu na serwerze:
- utworzenie pliku ```docker_compose```
- utworzenie plików ```dockerfile```
- pobranie gotowego projektu z repozytorium 
- uruchomienie narzędzia do konteneryzacji