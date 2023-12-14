#### Build the Linux version of the Flutter app in the Terminal
{:.no_toc}

To generate the needed Linux platform dependencies,
run the `flutter build` command.

```terminal
$ flutter build linux --debug
```

```terminal
Building Linux application...                                    31.4s
√  Built build/linux/x64/debug/bundle
```

{% comment %} Nav tabs {% endcomment -%}
<ul class="nav nav-tabs" id="vscode-to-vs-setup" role="tablist">
    <li class="nav-item">
        <a class="nav-link active" id="from-vscode-to-clion-tab" href="#from-vscode-to-clion" role="tab" aria-controls="from-vscode-to-clion" aria-selected="true">Start from VS Code</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" id="from-clion-to-vscode-tab" href="#from-clion-to-vscode" role="tab" aria-controls="from-clion-to-vscode" aria-selected="false">Start from CLion</a>
    </li>
</ul>

{% comment %} Tab panes {% endcomment -%}
<div class="tab-content">

<div class="tab-pane active" id="from-vscode-to-clion" role="tabpanel" aria-labelledby="from-vscode-to-clion-tab" markdown="1">

#### Start debugging with VS Code first {#vscode-linux}
{:.no_toc}

If you use VS Code to debug most of your code, start with this section.

##### Start the debugger in VS Code
{:.no_toc}

{% include docs/debug/debug-flow-vscode-as-start.md %}

{% comment %}
     !['Flutter app generated as a Linux app. The app displays two buttons to open this page in a browser or in the app'](/assets/images/docs/testing/debugging/native/url-launcher-app/linux.png){:width="50%"}
     <div markdown="1">{:.figure-caption}
     Flutter app generated as a Linux app. The app displays two buttons to open this page in a browser or in the app.
     </div>
{% endcomment %}

##### Attach to the Flutter process in CLion

For a detailed manual, have a look at the [documentation](https://www.jetbrains.com/help/clion/attach-to-process.html) of CLion.

1. To open the project solution file, go to
   **File** <span aria-label="and then">></span>
   **Open…**

1. Choose the `build/linux/` folder in your Flutter app directory.

{% comment %}
   ![Open File or Project dialog box in CLion 2023 with linux folder selected.](/assets/images/docs/testing/debugging/native/clion/choose-solution.png){:width="100%"}
   <div markdown="1">{:.figure-caption}
   Open File or Project dialog box in CLion 2023 with `linux` folder selected.
   </div>
{% endcomment %}

1. Go to **Run** > **Attach to Process…**.

   You can also press <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>5</kbd>.

1. From the **Attach to Process…** dialog box, choose `my_app`.

{% comment %}
   ![Selecting my_app from the Attach to Process dialog box](/assets/images/docs/testing/debugging/native/clion/attach-to-process-dialog.png){:width="100%"}
{% endcomment %}

   Press **Attach with Bundled GDB**.

   CLion starts monitoring the Flutter app.

{% comment %}
   ![CLion debugger running and monitoring the Flutter app](/assets/images/docs/testing/debugging/native/clion/debugger-active.png){:width="100%"}
{% endcomment %}

1. On some distribution of Linux you might get the **ptrace: Operation not permitted** error message.
   You can avoid this by running this command:

   ```terminal
   echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
   ```

</div>

<div class="tab-pane" id="from-clion-to-vscode" role="tabpanel" aria-labelledby="from-clion-to-vscode-tab" markdown="1">

#### Start debugging with CLion first
{:.no_toc}

If you use CLion to debug most of your code, start with this section.

##### Start the local Linux debugger
{:.no_toc}

1. To open the project solution file, go to
   **File** <span aria-label="and then">></span>
   **Open…**

1. Choose the `build/linux/` folder in your Flutter app directory.

{% comment %}
![Open File or Project dialog box in CLion 2023 with linux folder selected.](/assets/images/docs/testing/debugging/native/clion/choose-solution.png){:width="100%"}
   <div markdown="1">{:.figure-caption}
   Open File or Project dialog box in CLion 2023 with `linux` folder selected.
   </div>
{% endcomment %}

1. Set `my_app` as the startup project.
   In the **Solution Explorer**, right-click on `my_app` and select
   **Set as Startup Project**.

1. Click **Local Linux Debugger** to start debugging.

   You can also press <kbd>F5</kbd>.

   When the Flutter app has started, a console window displays
   a message with the Dart VM service URI. It resembles the following response:

   ```terminal
   flutter: The Dart VM service is listening on http://127.0.0.1:62080/KPHEj2qPD1E=/
   ```

1. Copy the Dart VM service URI.

##### Attach to the Dart VM in VS Code
{:.no_toc}

1. To open the command palette, go to
   **View** <span aria-label="and then">></span>
   **Command Palette...**

   You can also press <kbd>Cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>.

1. Type `debug`.

1. Click the **Debug: Attach to Flutter on Device** command.

{% comment %}
   !['Running the Debug: Attach to Flutter on Device command in VS Code.'](/assets/images/docs/testing/debugging/vscode-ui/screens/attach-flutter-process-menu.png){:width="100%"}
{% endcomment %}

1. In the **Paste an VM Service URI** box, paste the URI you copied
   from CLion and press <kbd>Enter</kbd>.

{% comment %}
   ![Alt text](/assets/images/docs/testing/debugging/vscode-ui/screens/vscode-add-attach-uri-filled.png)
{% endcomment %}

</div>
</div>
{% comment %} End: Tab panes. {% endcomment -%}
