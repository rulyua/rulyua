#android change package id command line
grep -ril . -e com.example.app --exclude-dir=.git | xargs sed -i '' -e 's/com.example.app/com.rulyua.memory_game/g'
