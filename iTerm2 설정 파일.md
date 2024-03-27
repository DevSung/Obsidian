export ZSH="$HOME/.oh-my-zsh"

ZSH_THEME="agnoster"

plugins=(
	git
	zsh-autosuggestions
)

source $ZSH/oh-my-zsh.sh

alias ll='ls -al'

prompt_context() {
  if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
    prompt_segment black default "%(!.%{%F{yellow}%}.)$USER"
  fi
}

prompt_context() {
  # Custom (Random emoji)
  emojis=("⚡️" "🔥"  "👑" "😎" "🐸" "🐵" "🦄" "🌈" "🍻" "🚀" "💡" "🎉" "🔑" "🚦" "🌙")
  RAND_EMOJI_N=$(( $RANDOM % ${#emojis[@]} + 1))
  prompt_segment black default "sungsin ${emojis[$RAND_EMOJI_N]} "
"~/.zshrc" 27L, 745B