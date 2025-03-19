## SonarQube

### Docker

#### Configuração para elasticsearch
Editar o arquivo /etc/sysctl.conf
Incluir a configuração:
vm.max_map_count=262144

Executar:
sudo systemctl --system

#### Rodar o Docker Compose
docker-compose up

#### Pré-requisito
SDK .NET
Java instalado na versão suportada pelo server, ou Java17 para o scanner versão 9.2.1

#### Instalação do sonar scanner
dotnet tool install --global dotnet-sonarscanner

#### Instalação do dotnet coverage
dotnet tool install --global dotnet-coverage

#### Comandos para coleta das informações (os dados de token e nome do projeto são gerados no sonarqube)
- dotnet sonarscanner begin /k:"key-do-projeto" /d:sonar.host.url="http://localhost:9000"  /d:sonar.token="token-do-projeto" /d:sonar.cs.vscoveragexml.reportsPaths=coverage.xml
- dotnet build
- dotnet-coverage collect 'dotnet test' -f xml  -o 'coverage.xml'
- dotnet sonarscanner end /d:sonar.token="token-do-projeto"

### Sites de Referência
https://docs.sonarsource.com/sonarqube-server/latest/analyzing-source-code/scanners/dotnet/introduction/?_gl=1*1ldxyic*_gcl_au*MTA5NDU2NDY5My4xNzQxNjMyNzQ5*_ga*MTc4MjUxMDg4LjE3NDE2MzI3NDg.*_ga_9JZ0GZ5TC6*MTc0MTg3ODMyMC4yLjAuMTc0MTg3ODMyMC42MC4wLjA.

https://www.nuget.org/packages/dotnet-sonarscanner

https://medium.com/@thiagoloureiro/an%C3%A1lise-de-c%C3%B3digo-com-sonarqube-docker-net-core-aad17147486a

