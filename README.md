# actinver-envoys-yamls
Se versionan los archivos config.yamls para los Envoy (GCP y On prem) del proyecto Apigee Actinver


Ubicacion de envoy-config.yaml en mig-internal-envoy-devqa-{id} (GCP Project: API-ACT-DEV-QA):
Este envoy server se conecta a los microservicios de istio en 10.156.200.238:80

/home/envoy/actinver-mig/envoy-config.yaml

Para administrar el envoy server sur (on prem) tenemos que tener permisos de SSH para conectarnos a la VM llamada instance-1 en el proyecto sdn-net-375917 de Actinver.
Una vez dentro nos conectamos via SSH con el siguiente comando: 
ssh adminux@ipEnvoyOnPrem (la contraseña debes solicitarla a algun administrador/usuario)

Existen dos Envoy config yamls: 
Una con los filtros para que funcione el remote service con la Apigee org la cual se encuentra en:

/home/adminux/apigee-envoy-files/apigee-remote-service-cli/samples/envoy-config.yaml

Ejecuta con:
sudo envoy -c envoy-config.yaml -l off --component-log-level http:debug,connection:debug --log-path /ubicacionDondequierasqueseguardenlogs

y la otra version (actualmente se ejecuta) que cuenta con filtro http y tcp:
/home/adminux/envoy/tcp-https-envoy-config-v2.yaml

Ejecuta con:
sudo envoy -c ..ubicaciondelarchivo/tcp-https-envoy-config-v2.yaml -l off --component-log-level http:debug,connection:debug --log-path /ubicacionDondequierasqueseguardenlogs
