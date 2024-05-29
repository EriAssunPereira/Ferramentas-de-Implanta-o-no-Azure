# Ferramentas-de-Implantaçâo-no-Azure

**Projeto: Ferramentas de Implantação no Azure**

Este projeto é focado em fornecer uma experiência prática com ferramentas de implementação, como o Azure DevOps e o Azure Resource Manager. Vamos dividir isso em módulos para facilitar a compreensão.

**Módulo 1: Azure DevOps**
O Azure DevOps é uma plataforma de entrega contínua que pode ser usada para automatizar compilações e implantação. Ele permite que as equipes planejem trabalhos, colaborem em códigos e implementem aplicativos.

```python
# Exemplo de código para criar um pipeline de build no Azure DevOps
from azure.devops.connection import Connection
from azure.devops.v5_1.build.models import BuildDefinition

connection = Connection(base_url='https://dev.azure.com/organizacao', creds=credentials)
client = connection.clients.get_build_client()

build_definition = BuildDefinition(
    name='Meu Pipeline',
    project='Meu Projeto',
    repository={'type': 'git', 'name': 'Meu Repositório'},
    process={'type': 2, 'yamlFilename': '/azure-pipelines.yml'}
)

client.create_definition(definition=build_definition, project='Meu Projeto')
```

**Módulo 2: Azure Resource Manager**
O Azure Resource Manager é uma ferramenta de gerenciamento de serviço que permite que você crie, atualize e exclua recursos da sua conta Azure. Ele permite que você gerencie e organize seus recursos.

```python
# Exemplo de código para criar um grupo de recursos no Azure Resource Manager
from azure.mgmt.resource import ResourceManagementClient

resource_client = ResourceManagementClient(credentials, subscription_id)

resource_group_params = {'location':'westus'}

resource_client.resource_groups.create_or_update('meuGrupoDeRecursos', resource_group_params)
```

Claro, aqui estão mais alguns exemplos de como você pode usar o Azure Resource Manager:

**1. Criando uma Máquina Virtual**
O Azure Resource Manager permite que você crie e gerencie máquinas virtuais. Aqui está um exemplo de como você pode criar uma máquina virtual:

```python
from azure.mgmt.compute import ComputeManagementClient
from azure.mgmt.compute.models import VirtualMachine

compute_client = ComputeManagementClient(credentials, subscription_id)

vm_params = {
    'location': 'westus',
    'hardware_profile': {
        'vm_size': 'Standard_D2_v2'
    },
    'storage_profile': {
        'image_reference': {
            'publisher': 'MicrosoftWindowsServer',
            'offer': 'WindowsServer',
            'sku': '2016-Datacenter',
            'version': 'latest'
        }
    },
    'os_profile': {
        'computer_name': 'meuComputador',
        'admin_username': 'admin',
        'admin_password': 'SenhaSegura123'
    },
    'network_profile': {
        'network_interfaces': [{
            'id': meu_nic.id,
        }]
    }
}

compute_client.virtual_machines.create_or_update(
    'meuGrupoDeRecursos',
    'minhaMaquinaVirtual',
    vm_params
)
```

**2. Listando todos os Recursos em um Grupo de Recursos**
Você pode usar o Azure Resource Manager para listar todos os recursos em um grupo de recursos específico. Aqui está um exemplo de como você pode fazer isso:

```python
from azure.mgmt.resource import ResourceManagementClient

resource_client = ResourceManagementClient(credentials, subscription_id)

for item in resource_client.resources.list_by_resource_group('meuGrupoDeRecursos'):
    print(item.name)
```

**3. Excluindo um Grupo de Recursos**
Você também pode usar o Azure Resource Manager para excluir um grupo de recursos. Aqui está um exemplo de como você pode fazer isso:

```python
from azure.mgmt.resource import ResourceManagementClient

resource_client = ResourceManagementClient(credentials, subscription_id)

resource_client.resource_groups.delete('meuGrupoDeRecursos')
```

Espero que esses exemplos ajudem a quem precisa entender melhor como usar o Azure Resource Manager para gerenciar seus recursos na Azure. Lembre-se, a prática é a chave para se tornar proficiente em qualquer tecnologia!
