# TOS-PreviewJetpackCompose

Lorsque vous utilisez des composants Jetpack Compose, vous avez la possibilité d'utiliser l'annotations ```@Preview()``` afin de prévisualiser le rendu de votre composant avant de lancer l'application et ainsi définir votre composant rapidement.

```kotlin
package com.example.magellangpt.ui.screens.conversation

import androidx.compose.foundation.lazy.LazyColumn
import androidx.compose.foundation.lazy.items
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.text.style.TextAlign
import androidx.compose.ui.tooling.preview.Preview
import com.example.magellangpt.domain.entities.conversation.Conversation
import com.example.magellangpt.domain.entities.conversation.Message
import com.example.magellangpt.domain.enums.UserType

@Composable
fun MessageList(
    modifier: Modifier,
    conversation: Conversation?
) {

    LazyColumn(
        modifier
    ) {
        if (conversation?.messages != null) {
            items(conversation.messages) { message ->
                MessageBox(message = message)
            }
        } else {
            items(1) {
                Text(
                    text = "Saisissez un message pour démarrer une conversation.",
                    textAlign = TextAlign.Center
                )
            }
        }
    }
}

@Preview(showBackground = true)
@Composable
fun ConversationListPreview() {

    val messages = listOf(
        Message("Qu'est-ce qui est jaune et qui attend ?", UserType.User),
        Message("Un citron pas pressé", UserType.Assistant),
        Message(
            "Voici une question un peu plus longue pour voir si tu es capable de répondre de manière assez responsive.",
            UserType.User
        ),
        Message("Oui bien sur que c'est responsive", UserType.Assistant)
    )

    MessageList(
        modifier = Modifier,
        conversation = Conversation(
            messages = messages
        )
    )
}
```

Vous aurez ensuite la possibilité de voir cette preview avec les options du panel droit sur Android Studio : 

<img width="361" alt="image" src="https://github.com/ThibautMoninDiiage/TOS-PreviewJetpackCompose/assets/104756641/8880e09f-117c-459a-ae4b-24d47f9f4919">

