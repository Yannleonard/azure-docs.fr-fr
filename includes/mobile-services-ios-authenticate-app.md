* Ouvrez **QSTodoListViewController.m** et ajoutez la méthode suivante. Remplacez *facebook* par *microsoftaccount*, *twitter*, *google* ou *windowsazureactivedirectory* si vous n’utilisez pas Facebook comme fournisseur d’identité.

```
        - (void) loginAndGetData
        {
            MSClient *client = self.todoService.client;
            if (client.currentUser != nil) {
                return;
            }

            [client loginWithProvider:@"facebook" controller:self animated:YES completion:^(MSUser *user, NSError *error) {
                [self refresh];
            }];
        }
```

* Remplacez `[self refresh]` dans `viewDidLoad` par ceci :

```
        [self loginAndGetData];
```

* Appuyez sur **Exécuter** pour démarrer l’application, puis ouvrez une session. Une fois connecté, vous devez être en mesure d’afficher la liste des tâches et d’effectuer des mises à jour.

<!---HONumber=Oct15_HO3-->