## Collection of our beloved SHELL functions.

### PR Guidelines :
<ul>
  <li>
    <details>
      <summary>Code Template :</summary>
      <pre>Use below template and add it to specific section in README</pre>
      <ul>
        <pre>
        &lt;li&gt;
          &lt;details&gt;
            &lt;summary&gt; function name : short description &lt;/summary&gt;
            &lt;br&gt;
            &lt;pre&gt;SHELL: BASH/FISH/ZSH&lt;/pre&gt;
            &lt;pre&gt;USAGE: how you use the function&lt;/pre&gt;
            &lt;ul&gt;
              &lt;li&gt;
                &lt;pre&gt;
                  Your Code goes here ...
                &lt;/pre&gt;
              &lt;/li&gt;
            &lt;/ul&gt;
          &lt;/details&gt;
        &lt;/li&gt;
        </pre>
      </ul>
    </details>
  </li>
  <li>
    Commit msg: <pre>function_name: short description</pre>
  </li>
</ul>

### Functions :
<ul>
  <li>
    <details>
      <summary> v : for viewing files in general.</summary>
      <br>
      <pre>SHELL: Fish</pre>
      <pre>USAGE: v anyfile</pre>
      <ul>
        <li>
          <pre>
            function v
              if [ -z "$argv" ]
                echo "Do pass a file to view !"
              else if [ -d "$argv" ]
                echo Files Count: (count $argv/*); ls -sh $argv
              else if string match -r ".jpg|.png|.svg" $argv &> /dev/null
                kitty +kitten icat $argv
              else if string match -r ".mp4|.mkv|.mp3" $argv &> /dev/null
                mpv $argv
              else if string match -q "*.docx" $argv
                catdocx $argv | bat
              else if string match -q "*.pdf" $argv
                zathura $argv &> /dev/null
              else
                bat $argv
              end
            end
          </pre>
        </li>
      </ul>
    </details>
  </li>
  <li>
    <details>
      <summary>invalid_cmd: msg if a random text is entered </summary>
      <br>
      <pre>SHELL: Fish</pre>
      <pre>USAGE: any random text asdasd</pre>
      <ul>
        <li>
          <pre>
	          function __fish_command_not_found_handler --on-event fish_command_not_found
              set -l exit_string "You know what you are doing, right ?" "Are you sure about that ?" "Sorry can't find what you are looking for :(" "IDK what you mean !" "Invalid command !" "You in the right mood mate ?"
              set index (random 1 6)
	            printf '%s\n' $exit_string[$index]
	          end
          </pre>
        </li>
      </ul>
    </details>
  </li>
</ul>


### License:
```
Copyright © 2021 Creator54<hi.creator54@gmail.com>

Code here is free software licensed under MIT.

This code is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY;
without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the MIT LICENSE for more details.
```
[Read Details](https://github.com/creator54/shell.rc/blob/main/LICENSE)
