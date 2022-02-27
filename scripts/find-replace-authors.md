Command to find/replace within all subfolders (e.g., to find and replace 'Sam Harper' with '**Sam Harper**' in the publication files

find . -type f -name "*.rb" | xargs sed -i '' 's/string1/string2/g'
