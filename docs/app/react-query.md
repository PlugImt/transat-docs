# React Query

React Query (TanStack Query) est une bibliothèque de gestion de l'état (_state management_).

## Comment ça marche?

React Query permet de simplifier la gestion des données asynchrones, concrètement, il permet de simplifier:

- la récupération de données avec les `Queries`
- la création, mise à jour, suppression de données avec les `Mutations`

React Query à l'aide d'un client commun (le `queryClient`) pour gérer les données, qui gère le cache, les requêtes, les mutations, etc. Il est stocké dans un Contexte (avec `QueryClientProvider`) et accessible partout dans l'application.

## Les Queries

Une `Query` est une fonction asynchrone qui récupère des données.

```ts
const { data, isLoading, error } = useQuery({
  queryKey: ["todos"],
  queryFn: () => fetch("/api/todos").then((res) => res.json()),
});
```

Dans cet exemple, la `Query` est une fonction asynchrone qui récupère des données depuis une API. On peut observer que la `Query` est composée de plusieurs propriétés. Premièrement, la clé `queryKey` est une tableau unique de clés pour identifier la `Query` dans le cache interne de React Query. Enfin, `queryFn` est la fonction asynchrone qui récupère les données en soit.

Comme vous pouvez le voir, en seulement 3 lignes de code, on gère:

- l'état de chargement (`isLoading`)
- les erreurs (`error`, il existe aussi `isError`)
- les données récupérées (`data`)
- aussi:
  - réessai en cas d'erreur (3 fois par défaut)
  - refetch par:
    - intervalle de temps
    - focus de la page
    - invalidation manuelle de la query

React Query intègre un cache, c'est-à-dire que les données récupérées sont mises en cache et réutilisées si la même `Query` (avec la même `queryKey`) est appelée à nouveau dans un autre composant.

Cela permet d'éviter d'avoir des useState et des useEffect pour gérer les données.

## Les Mutations

Une `Mutation` est une fonction asynchrone qui **crée**, **met à jour** ou **supprime** des données (en gros, des... mutations de données). Une différence majeure entre les `Queries` et les `Mutations` est qu'une query est lancée dès que possible, alors qu'une mutation est lancée manuellement (avec `mutate`).

```ts
const queryClient = useQueryClient();

const { mutate } = useMutation({
  mutationFn: (newTodo) =>
    fetch("/api/todos", { method: "POST", body: JSON.stringify(newTodo) }),
  onSuccess: () => {
    queryClient.invalidateQueries({ queryKey: ["todos"] });
  },
});
```
