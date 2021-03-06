# Access management

Yandex.Cloud users can only perform operations on resources that are allowed by the roles assigned to them.
If a user doesn't have any roles assigned, almost all operations are forbidden.

To allow access to resources of the [!KEYREF container-registry-short-name] service (registries and Docker images),
assign applicable roles to the user from the list below. For now, a role can only be assigned to a parent resource (folder or cloud), whose roles are inherited by nested resources.

> [!NOTE]
> 
> For more information about role inheritance, see [[!TITLE]](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) in the [!KEYREF resmgr-full-name] documentation.

## Assigning roles

To assign a role to a user:

[!INCLUDE [grant-role-console](../../_includes/grant-role-console.md)]

## Roles

The list below shows all roles that are considered when verifying access rights in the [!KEYREF container-registry-short-name] service.

### Service roles

_Service roles_ are roles that allow access to the resources of a particular service.

[!INCLUDE [cloud-roles](../../_includes/cloud-roles.md)]

### Primitive roles

You can assign primitive roles to any resource in any service.

#### [!KEYREF roles-viewer]

A user with the `[!KEYREF roles-viewer]` role can view information about resources, for example, view a list of registries or pull a Docker image.

#### [!KEYREF roles-editor]

A user with the `[!KEYREF roles-editor]` role can manage Docker images, for example, push or delete them.

In addition, the `[!KEYREF roles-editor]` role includes all permissions of the `[!KEYREF roles-viewer]` role.

#### [!KEYREF roles-admin]

A user with the `[!KEYREF roles-admin]` role can manage access rights to resources, for example, allow other users to view registries or work with Docker images.

In addition, the `[!KEYREF roles-admin]` role includes all permissions of the role of `[!KEYREF roles-editor]`.

